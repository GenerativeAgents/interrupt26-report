# Observing and Testing CX Agents

- 日付: 2026年5月14日
- 時間: 10:00 AM-10:20 AM
- 登壇者: Carlos Pereira
- 音声: [Observing and Testing CX Agents.m4a](Observing%20and%20Testing%20CX%20Agents.m4a)
- 文字起こし: [Observing and Testing CX Agents_original.txt](Observing%20and%20Testing%20CX%20Agents_original.txt)

## 要約

このセッションは、Cisco の customer experience / support 領域で agent を本番運用する際に、production feedback をどのように観測し、テストへ戻していくかを扱っていた。前日の Cisco セッションが agent teammate の全体像や SmithDB の背景を語っていたのに対し、Day 2 では運用中の signal を改善 loop に変える方法に焦点があった。

重要な見立ては、ユーザーの thumbs down、エラー、複雑な escalation、confusing user interaction、production trace はすべて「無視できない signal」だということだった。support 領域では同時に大量の cases が走るため、人間だけで個別確認するのは現実的ではない。そこで、production traces を LangSmith で捕捉し、AI agent が分析・診断・クラスタリングし、人間がレビューして PR にする loop が紹介された。

セッションでは、reactive な feedback handling と proactive な regression prevention の両方が語られた。reactive には、実際に発生した失敗やユーザーフィードバックから修正候補を作る。proactive には、出荷前に subject matter experts とともに regression tests を作り、既知の失敗を再発させないようにする。

## 重要ポイント

- thumbs down、trace、error、confusing interaction はすべて改善 signal。
- support scale では、人手の triage だけでは production feedback を処理しきれない。
- LangSmith traces と MCP / coding agent を使い、失敗分析から修正PRまでの距離を縮める。
- 同じ原因に属する failing traces を clustering し、重複PRを避ける発想が重要。
- 改善 loop には AI による分析と human review の両方が必要。
- 出荷前の regression tests と、出荷後の production feedback の両輪で品質を上げる。
