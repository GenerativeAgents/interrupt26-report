# Transcription Workflow

このリポジトリで録画・音声ファイルから書き起こしを作るための手順です。
`recap_0513` のMP4書き起こしで使った方式を、`sessions` の `.m4a` ファイルにも再利用します。

## 前提

- macOS
- Homebrew
- `uvx`
- `git-lfs`
- `ffmpeg`

未導入の場合は以下を実行します。

```sh
brew install ffmpeg git-lfs
git lfs install
```

## 基本コマンド

`mlx-whisper` を `uvx` 経由で実行し、テキスト、字幕、タイムスタンプ、JSONをまとめて出力します。

```sh
uvx --from mlx-whisper mlx_whisper \
  "入力ファイルパス" \
  --model mlx-community/whisper-large-v3-turbo \
  --language ja \
  --output-dir "出力ディレクトリ" \
  --output-name "出力ファイル名" \
  --output-format all \
  --verbose False
```

生成される主なファイルは以下です。

- `.txt`: 読み物として扱いやすいプレーンテキスト
- `.srt`: 字幕ファイル
- `.vtt`: WebVTT字幕ファイル
- `.tsv`: 開始時刻、終了時刻、テキストを含む表形式
- `.json`: セグメント、トークン、タイムスタンプなどを含む詳細データ

## sessionsでの実行例

たとえば `sessions/Day1 keynote.m4a` を書き起こす場合は以下です。

```sh
uvx --from mlx-whisper mlx_whisper \
  "sessions/Day1 keynote.m4a" \
  --model mlx-community/whisper-large-v3-turbo \
  --language ja \
  --output-dir sessions \
  --output-name "Day1 keynote" \
  --output-format all \
  --verbose False
```

既存の `_original.txt` を更新したい場合は、生成された `.txt` の内容を確認してからリネームまたは差し替えます。

```sh
mv "sessions/Day1 keynote.txt" "sessions/Day1 keynote_original.txt"
```

複数ファイルを処理する場合も、まず1ファイルずつ実行して品質を確認します。固有名詞や製品名は誤認識されやすいため、セッション要約に使う前に必ず目視確認します。

## 出力後の整形

生成ファイルに末尾空白や余分な空行が入ることがあるため、コミット前に整えます。

```sh
perl -0pi -e 's/\n+\z/\n/' sessions/*.srt sessions/*.vtt
perl -pi -e 's/[ \t]+$//' sessions/*.tsv
git diff --check
```

対象ファイルが存在しない場合はシェルがエラーにすることがあります。その場合は存在する拡張子だけを指定して実行します。

## 大容量ファイルの扱い

MP4など大きな録画ファイルを追加する場合はGit LFSで管理します。

```sh
git lfs track "*.mp4"
git add .gitattributes
```

コミット前に、動画本体が通常のGit差分ではなくLFSポインタになっていることを確認します。

```sh
git lfs ls-files
git diff --cached -- "対象の動画ファイル.mp4"
```

差分に以下のような3行のポインタが表示されれば正常です。

```text
version https://git-lfs.github.com/spec/v1
oid sha256:...
size ...
```

## Red Teamレビュー

このリポジトリでは、ファイル変更後にRed Teamレビューを行ってからコミット・プッシュします。

最低限、以下を確認します。

- 書き起こしに明らかな固有名詞の誤りや誤解を招く箇所がないか
- セッション要約へ転記する場合、内容が発話と対応しているか
- 追加ファイルに意図しない一時ファイルや不要な生成物が含まれていないか
- 大容量ファイルがGit LFS管理になっているか
- 機密情報らしき文字列が含まれていないか
- Markdownや字幕ファイルのリンク、見出し、空白に問題がないか

確認用コマンド例です。

```sh
git status --short --branch
git diff --cached --stat
git diff --check
rg -n "(sk-[A-Za-z0-9]|AKIA[0-9A-Z]{16}|BEGIN (RSA|OPENSSH|EC|PRIVATE)|password|PASSWORD|api[_-]?key|secret)" sessions recap_0513 || true
```

`json` 内の `tokens` のようなWhisper由来のフィールド名は機密情報ではありません。ヒットした文字列は文脈を確認して判断します。

## コミットとプッシュ

レビュー後、関連ファイルだけをステージしてコミットします。

```sh
git add 対象ファイル
git commit -m "Add session transcript"
git push origin main
```
