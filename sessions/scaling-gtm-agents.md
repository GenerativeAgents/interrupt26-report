# Scaling GTM Agents

- 日付: 2026年5月13日
- 時間: 11:20 AM-11:40 AM
- 登壇者: Jeff Barg
- 関連ファイル名: Clay _ scaling gtm agents
- 音声: [Clay _ scaling gtm agents.m4a](Clay%20_%20scaling%20gtm%20agents.m4a)
- 文字起こし: [Clay _ scaling gtm agents_original.txt](Clay%20_%20scaling%20gtm%20agents_original.txt)

## 要約

Clay のセッションでは、GTM agents を大規模に運用するための実践的な課題が語られた。単にメール文面を生成するだけでは leverage が低く、より価値があるのは market layer 全体をスキャンし、資金調達、採用、公開情報、顧客データなどの signal から「いつ・誰に・どの文脈で outreach すべきか」を判断することだと説明された。

運用上の課題として、まず infrastructure reliability が挙げられた。agent は外部サービスや browser を待つ時間が長く、単純な Lambda 型の実行では cold start や failure recovery が問題になりやすい。durable execution、checkpoint、periodic task、LangGraph / LangSmith 的な実行基盤が重要になる。

次に capacity / cost の問題が取り上げられた。GTM workload は大量に並列実行されるため、inference provider の throttle に合わせて送信量を調整し、capacity を最大化する仕組みが必要になる。さらに prompt caching や provider strategy が cost に大きく効くことも紹介された。

品質面では、良い context、良い dataset、online evaluation が不可欠だと説明された。Clay は go-to-market data を統合し、audiences / signals / playbooks を通じて agent がよりよい判断を行う方向へ進んでいる。

## 重要ポイント

- GTM agents の本質は email generation ではなく、market signal を読んだタイミング・文脈判断。
- 大量実行には durable execution と failure recovery が必要。
- provider throttle に合わせた adaptive capacity management が重要。
- prompt caching や provider strategy は cost を大きく左右する。
- agent quality は context、dataset、online eval、observability に依存する。
- 将来的には agent が過去の試行と context から playbook を改善する flywheel を目指す。
