# How Lyft Builds Evals That Actually Matter in Production

- 日付: 2026年5月13日
- 時間: 12:00 PM-12:20 PM
- 登壇者: Nick Ung
- 関連ファイル名: Lyft
- 音声: [Lyft.m4a](Lyft.m4a)
- 文字起こし: [Lyft_original.txt](Lyft_original.txt)

## 要約

Lyft のセッションでは、customer care AI agents を production で安全に拡張するための eval system が紹介された。Lyft では月間 7,900 万 trips、月間 270,000 件規模の AI intervention があり、AI resolution rate は 35% と説明された。refund、damage claim、driver / rider support など、実運用で複雑な判断を行う agents を扱っている。

登壇者は、AI engineering も traditional ML engineering と同じように offline evaluation を重視すべきだと強調した。ユーザーをテストデータにするのではなく、launch 前に simulator、mocked MCP data、synthetic user、rubric-based evaluator を使って品質ゲートを作る。offline simulator では model-based user が会話 trajectory を生成し、state of the world や user intent を YAML で定義する。

評価設計では、単なる helpfulness や conciseness のような scalar score では actionable insight になりにくいと説明された。代わりに、agent が達成すべき task と失敗条件を明確にした rubric を作り、失敗時にどの prompt / tool / logic を直すべきかが分かるようにする。

また、LLM-as-judge も ML model と同じように扱い、human labels / domain expert labels を使って calibrate する必要があると述べた。LangSmith の traces、online runs、automation、annotation queue を使い、production feedback を eval improvement と harness improvement につなげている。

## 重要ポイント

- production AI agents には offline eval が品質ゲートとして必要。
- simulator は model user、mocked world state、MCP output、conversation trajectory を組み合わせる。
- eval rubric は task-oriented にし、失敗が actionable になるよう設計する。
- LLM-as-judge は human labels で校正する。
- synthetic users は現実のユーザーより丁寧すぎるため、production-like behavior に近づける必要がある。
- LangSmith traces と annotation queue が continuous improvement の入力になる。
