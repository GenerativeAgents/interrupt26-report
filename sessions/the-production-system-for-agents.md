# The Production System for Agents

- 日付: 2026年5月13日
- 時間: 11:40 AM-12:00 PM
- 登壇者: Kordel France, Ravi Chandu Ummadisetti
- 関連ファイル名: Toyota _ the production system for agents
- 音声: [Toyota _ the production system for agents.m4a](Toyota%20_%20the%20production%20system%20for%20agents.m4a)
- 文字起こし: [Toyota _ the production system for agents_original.txt](Toyota%20_%20the%20production%20system%20for%20agents_original.txt)

## 要約

Toyota のセッションでは、enterprise 内で AI agents を量産するための platform approach と、Toyota Production System の考え方を agent 開発へ移植する視点が紹介された。Toyota では 65,000 人規模・複数工場・多様な data source があり、各チームが個別に chatbot を作ると security / governance / integration が崩れる。そこで、共通 platform と標準 pipeline によって agent を短期間で構築できる仕組みを整えた。

初期には 1 つの agent 構築に 6 人の engineer と 6 か月が必要だったが、platform 化により 4 日程度で構築できるようになったと説明された。重要な構成要素は、dynamic graph、shared security / integration layer、LangChain / LangGraph / Deep Agents、MCP-compatible tool layer、enterprise skills library、structured / unstructured data から自動生成される skills。

ユースケースとして、製造ラインの問題解決、過去の研究・設計知識の検索、設計支援などが紹介された。agent が Toyota の長年の institutional knowledge にアクセスできることで、現場の意思決定や問題解決の速度を上げる。

後半では、Toyota Production System の `andon`、`kaizen`、`jidoka`、`genchi genbutsu` を LangSmith / LangGraph / traces と対応づけた。LangSmith は agent の状態を見える化する `andon`、traces は問題の根本原因へ行く `genchi genbutsu`、LangGraph は human-in-the-loop を含む `jidoka` 的な仕組みとして語られた。

## TPS の4つの特徴と agent 開発への対応

### 1. Andon: 状態を即座に見える化する

Toyota Production System における `andon` は、製造ラインの異常や状態をすぐに見える化し、必要な人がすぐに対応できるようにする仕組み。登壇者は、LangSmith が agent 開発における andon の役割を担うと説明していた。

agent production では、どの tool call が成功しているか、どの user flow が詰まっているか、どの機能を次の PR / release で直すべきかを、個別ログを掘り続けなくても把握できる必要がある。LangSmith の observability は、複数 agent の挙動、失敗、user frustration point を横断して見える化し、engineer が改善対象を素早く判断するための production board になる。

agent 開発への示唆:

- agent fleet 全体の health、tool call、latency、failure、user outcome を一覧できることが重要。
- 問題発生時に「どこで止まったか」をすぐ見つけられる observability が、production agent の運用速度を決める。
- Andon は単なる dashboard ではなく、改善アクションへつながる signal layer として捉えるべき。

### 2. Kaizen: 小さく継続的に改善する

`kaizen` は、急激な一発改善ではなく、小さく、着実で、継続的な改善を積み上げる思想として説明された。登壇者は、software engineering culture の PR や frequent updates と kaizen を対応づけ、LangChain / LangSmith の ecosystem そのものも macro level で継続的に改善されていると語っていた。

agent の世界では、kaizen はさらに micro level でも起きる。agent は output を観察し、評価し、より良い final response を出すように反復する。LangSmith Engine のような仕組みは、production traces から issue を拾い、prompt、skills、code、evals を少しずつ直していくことで、agent behavior を継続的に改善する。

agent 開発への示唆:

- production agent は launch して終わりではなく、trace / eval / feedback をもとに改善し続ける対象。
- 大きな redesign よりも、小さな prompt fix、tool fix、skill update、eval addition を高頻度に積む方が現実的。
- regression を避けるため、改善は eval とセットで行う必要がある。

### 3. Jidoka: 人間の判断を残した自働化

`jidoka` は、文字通りには「人の手を備えた自働化」と説明されていた。登壇者は、LangGraph がこの考え方をよく体現していると述べた。つまり、繰り返しの多い処理や細かな制御は自動化しつつ、engineer や domain expert は loop から外れない。

agent production では、すべてを完全自動化すると risk が高い。financial transaction、customer messaging、compliance-sensitive response、high-impact tool call など、人間の確認が必要な場面がある。LangGraph / Deep Agents の human-in-the-loop は、approval、edit、reject、clarification といった decision point を workflow 内に組み込むことで、automation と human judgment の責任分界を作る。

agent 開発への示唆:

- agent は自律的に動くほど、どこで人間が介入するかを設計する必要がある。
- Human-in-the-loop は後付けの安全装置ではなく、workflow の一部として設計する。
- Jidoka 的な設計では、automation は人間を置き換えるだけでなく、人間が品質を守れる位置に残る。

### 4. Genchi Genbutsu: 現地現物で原因を見る

`genchi genbutsu` は「現地に行き、現物を見て、根本原因を理解する」考え方として説明された。製造ラインの問題を遠隔の会議室だけで推測するのではなく、現場に行って実際の hardware と状況を見るという発想。

agent 開発では、これに相当するのが traces。ある query、tool call、intermediate step、final answer の全経路を trace として確認できることで、engineer は推測ではなく実際の agent behavior を見て原因を追える。登壇者は、traces が root cause analysis の直接的な手段であり、logs を延々と探す代わりに問題箇所へ直接向かえると説明していた。

agent 開発への示唆:

- agent の失敗は final answer だけでは原因が分からないため、intermediate steps と tool calls を追える trace が必須。
- `genchi genbutsu` 的な運用では、推測で prompt を直すのではなく、実際の production trace を見て直す。
- trace は debugging だけでなく、eval dataset、ground truth examples、LangSmith Engine の改善 loop の入力にもなる。

## 重要ポイント

- enterprise agent 量産には、個別 chatbot ではなく共通 platform が必要。
- Toyota は agent 構築期間を 6 か月から 4 日へ短縮したと説明。
- skills を共有・自動生成し、MCP-compatible tool layer で安全に tool access を提供。
- LangSmith / LangGraph / Deep Agents を production system の基盤として活用。
- Toyota Production System の原則は agent manufacturing にも応用できる。
- `andon` は LangSmith observability、`kaizen` は trace / eval による継続改善、`jidoka` は human-in-the-loop、`genchi genbutsu` は traces に対応する。
- traces は root cause analysis のための `genchi genbutsu` 的な役割を持つ。
