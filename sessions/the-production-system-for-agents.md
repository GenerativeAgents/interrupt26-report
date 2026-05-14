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

## 重要ポイント

- enterprise agent 量産には、個別 chatbot ではなく共通 platform が必要。
- Toyota は agent 構築期間を 6 か月から 4 日へ短縮したと説明。
- skills を共有・自動生成し、MCP-compatible tool layer で安全に tool access を提供。
- LangSmith / LangGraph / Deep Agents を production system の基盤として活用。
- Toyota Production System の原則は agent manufacturing にも応用できる。
- traces は root cause analysis のための `genchi genbutsu` 的な役割を持つ。
