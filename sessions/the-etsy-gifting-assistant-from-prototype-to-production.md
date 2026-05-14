# The Etsy Gifting Assistant: From Prototype to Production

- 日付: 2026年5月14日
- 時間: 10:50 AM-11:10 AM
- 登壇者: Derrick Kondo
- 音声: [The Etsy Gifting Assistant.m4a](The%20Etsy%20Gifting%20Assistant.m4a)
- 文字起こし: [The Etsy Gifting Assistant_original.txt](The%20Etsy%20Gifting%20Assistant_original.txt)
- 関連リンク: [dkondo/agent-tackle-box](https://github.com/dkondo/agent-tackle-box)

## 要約

Etsy のセッションは、gift discovery という consumer experience に agent を入れる事例だった。Etsy は handcrafted / vintage items を扱う marketplace であり、商品情報は structured catalog だけではなく、seller が書いた説明、画像、視覚的な特徴、文脈に依存する。特に gift search は、買い手が「誰に贈るか」は分かっていても「何を贈るか」は明確でないことが多く、会話しながら意図を明確にしていく agent と相性がよい。

実装面では、LangGraph / LangChain を使って agent を構成し、search listings、user profile、memory などの tools / skills を扱う構成が紹介された。初期設計では simple な ReAct 風の構成から始め、reliability、memory management、latency、evaluation の課題に対応していった。

reliability では、同じ tool call を繰り返す問題に対して middleware で repeated tool calls を検知し、severity に応じて介入する仕組みが紹介された。また、listing ID hallucination に対しては、tool が返した observed IDs と model が最終的に使った IDs を照合し、存在しない ID を弾く deterministic check を入れていた。

memory management では、agent が重要な shopper / gift context を落とす問題があり、debugging / observability tooling が重要になった。関連して、Derrick Kondo 氏の `agent-tackle-box` は AI agents 開発向けの toolkit で、LangGraph / LangChain agents を terminal 上で debug する `agent-debugger` を含む。state、messages、tool calls、store snapshots、semantic breakpoints、Python-level debugging を 1 つの Textual UI で扱える。

evaluation では、trajectory evaluation と outcome evaluation の両方が扱われた。unit / integration test に加えて、agent が期待した tool を呼んだか、推薦された listings が shopper profile と合っているかを LLM judge や human-aligned dataset で評価する構成が語られた。

## 重要ポイント

- gift discovery は、会話を通じて曖昧な意図を具体化する agent と相性がよい。
- marketplace agent では、商品説明、画像、seller context、buyer profile、memory を統合する必要がある。
- repeated tool calls や listing ID hallucination には、middleware / deterministic checks が効く。
- model memory management の問題を追うには、agent state と tool calls を可視化できる debug tooling が重要。
- evaluation は trajectory と outcome の両方を見る必要がある。
- prototype から production へ進めるには、同じ serving path を offline evaluation と online execution の両方で使い、offline / online skew を避けることが重要。
