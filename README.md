# interrupt26-report

## イベント情報

- イベント名: Interrupt 2026 - The Agent Conference by LangChain
- 開催日: 2026年5月13日-14日
- 会場: The Midway, San Francisco
- 住所: 900 Marin St., San Francisco, CA
- 公式サイト: https://interrupt.langchain.com/
- 概要: AI agents の次を形づくる実践者向けカンファレンス。プロダクション環境で agents を展開している業界リーダーやチームの知見、実装事例、ワークショップを通じて、agents の構築・トレース・評価について学ぶ。
- 参加規模: 1,000人以上の practitioners が参加
- チケット: Sold out

### 主な内容

- 業界リーダーによる keynotes
- Clay、Rippling、Workday などの AI チームによる実運用の学び
- LangChain チームによる hands-on workshops
- builders 同士の交流、social hour、afterparty

## タイムテーブル

公式 agenda: https://interrupt.langchain.com/event-agenda

### Day 1: 2026年5月13日

| 時間 | セッション | 登壇者 |
| --- | --- | --- |
| 8:00 AM-9:30 AM | Registration, Breakfast & Sponsors | - |
| 9:30 AM-10:30 AM | [Keynote](sessions/day1-keynote.md) | Harrison Chase, Ankush Gola |
| 10:30 AM-10:50 AM | [Building Frontier CX Agents](sessions/building-frontier-cx-agents.md) | Carlos Pereira |
| 10:50 AM-11:20 AM | Break | - |
| 11:20 AM-11:40 AM | [Scaling GTM Agents](sessions/scaling-gtm-agents.md) | Jeff Barg |
| 11:40 AM-12:00 PM | [The Production System for Agents](sessions/the-production-system-for-agents.md) | Kordel France, Ravi Chandu Ummadisetti |
| 12:00 PM-12:20 PM | [How Lyft Builds Evals That Actually Matter in Production](sessions/how-lyft-builds-evals-that-actually-matter.md) | Nick Ung |
| 12:20 PM-1:40 PM | Lunch | - |
| 1:40 PM-2:00 PM | [Make Legal Write Your Evals](sessions/make-legal-write-your-evals.md) | Philipp Comans |
| 2:00 PM-2:20 PM | [Introducing Managed Deep Agents](sessions/introducing-managed-deep-agents.md) | Sydney Runkle, Victor Moreira |
| 2:20 PM-2:40 PM | [How We Built It](sessions/how-we-built-it.md) | Ben Tannyhill, Vivek Trivedy |
| 2:40 PM-3:10 PM | Break | - |
| 3:10 PM-3:30 PM | Building Deep Agent Sidekick | Omri Bruchim |
| 3:30 PM-3:50 PM | Intelligent Agents in Aviation | Nico Venegas, Claudio Urbina Lara |
| 3:50 PM-4:10 PM | Break | - |
| 4:10 PM-4:40 PM | Agents in the Enterprise | Aaron Levie, Harrison Chase |
| 4:40 PM-5:00 PM | Lessons Learned Building Rippling AI | Senthil Sundaram, Akash Ashok |
| 5:00 PM | Day 1 Reception: Sponsored by Fireworks | - |

### Day 2: 2026年5月14日

| 時間 | セッション | 登壇者 |
| --- | --- | --- |
| 8:30 AM-9:30 AM | Registration, Breakfast & Sponsors | - |
| 9:30 AM-10:00 AM | Keynote | Harrison Chase, Brace Sproul, Caroline di Vittorio |
| 10:00 AM-10:20 AM | Observing and Testing CX Agents | Carlos Pereira |
| 10:20 AM-10:50 AM | Break | - |
| 10:50 AM-11:10 AM | The Etsy Gifting Assistant: From Prototype to Production | Derrick Kondo |
| 11:10 AM-11:30 AM | 60% Faster Time-to-Interview: Transforming Hiring with AI Agents with LangChain | Shang Liu, Tracy He |
| 11:30 AM-11:40 AM | Run Untrusted Agent Code with LangSmith Sandboxes | Mukil Loganathan |
| 11:40 AM-1:00 PM | Lunch | - |
| 1:00 PM-1:30 PM | Future of AI Agents | Andrew Ng, Harrison Chase |
| 1:30 PM-2:00 PM | Agents in the Enterprise | Chirantan (CJ) Desai, Harrison Chase |
| 2:00 PM-2:20 PM | Building AI for Healthcare | Janie Lee |
| 2:20 PM-2:50 PM | Break | - |
| 2:50 PM-3:10 PM | Building Pat, the AI Pocket Analyst Tool | Brendan McManus, Santi Weight, Michael Ran |
| 3:10 PM-3:30 PM | Building Developer Support Agents | Evan Kormos |
| 3:30 PM-4:00 PM | The Return of the Data Scientist | Shreya Shankar, Hamel Husain |
| 4:00 PM | Day 2 Afterparty: Sponsored by Focused | - |

## リリーストピック

1. ✅ LangSmith Engine
2. ✅ SmithDB
3. ✅ Sandboxes
4. ✅ Managed Deep Agents
5. ✅ LLM Gateway
6. ✅ Context Hub
7. ✅ Deep Agents 0.6

### 1. LangSmith Engine

LangSmith Engine は、LangSmith の trace を起点に agent の継続改善ループを回すための機能。繰り返し発生する失敗を検出し、原因を診断し、修正案・回帰防止用 evaluator・offline evaluation 用の dataset examples までつなげる。GitHub repository を接続すると、Deep Agents / LangChain / LangGraph で作られた agent に対して修正 PR の提案もできる。

ポイント:

- production traces から recurring issue を自動検出
- root cause の診断、proposed fix、suggested evaluator を提示
- 問題が再発した場合に issue を reopen する closed-loop 改善
- trace から ground truth dataset examples を生成し、offline eval に接続

セッション補足:

- `How we built it` では、Engine の初期課題として「意味のある issue を見つけ、actionable な単位へ蒸留すること」が重要だと説明されていた。単に trace から問題を大量に見つけるのではなく、修正対象として扱える粒度に落とし込む設計がポイント。
- Engine は LangChain 製品群を組み合わせて動いており、Deep Agents、Sandboxes、LangSmith Deployment を使いながら、production trace と agent source code を入力にして問題診断・修正案生成へつなげる。
- trace は「本番で agent がどう振る舞ったか」を見る最重要入力として扱われ、必要に応じて condensed / summarized trace を使って調査する構成になっている。
- 公式ブログ `How My Agents Self-Heal in Production` でも、deploy 後の regression detection、triage agent、Open SWE による PR 作成までを自動化する self-healing loop が紹介されており、Engine が目指す「production signal から修正へつなぐ」方向性と重なる。

参考:

- https://docs.langchain.com/langsmith/engine
- https://www.langchain.com/blog/production-agents-self-heal/

### 2. SmithDB

SmithDB は、LangSmith の self-hosted changelog 上で確認できる LangSmith backend / data layer 側の新しい基盤要素。changelog では SmithDB-backed comparison view endpoints、SmithDB shadow、ClickHouse と SmithDB の dual-write / parallel write、SmithDB operations の async retry などが言及されている。Andrew Lamb 氏の X 投稿でも、SmithDB が Apache DataFusion でできていることが宣言されている。セッション情報では、SmithDB は Apache DataFusion と Vortex を土台にした Rust 製のデータ基盤として説明されていた。LangSmith の trace / dataset / comparison view 周辺をより高速・堅牢にするための analytical data layer と読める。

ポイント:

- comparison view を SmithDB-backed endpoint として提供
- ClickHouse ingestion と SmithDB dual-write / parallel write により ingestion latency を改善
- SmithDB shadow による dataset view の filtering / querying を強化
- SmithDB operation の async retry / error handling を追加
- Apache DataFusion を query engine として利用し、Rust / Apache Arrow ベースの高速な analytical query execution を活用
- Vortex のような extensible columnar file format と組み合わせ、trace に特化した indexing、query planning、execution plan、storage layout を追加している

セッション補足:

- `Cisco` セッションでは、SmithDB は trace observability のために purpose-built された基盤として説明され、以前より 6x-15x 高速になったという文脈で紹介されていた。
- 同セッションでは、全体が Rust で書かれ、2 つの open source project を基盤にしていると説明されていた。1 つ目が Apache DataFusion、2 つ目が extensible file format の Vortex。
- Apache DataFusion は公式ドキュメント上でも Rust 製の extensible query engine と説明され、Apache Arrow を in-memory format とし、SQL / DataFrame API、vectorized / multithreaded / streaming execution、custom data sources / functions / operators / optimizer passes などを提供する。
- SmithDB はこの基盤の上に、trace search 向けの indexing、custom query planning / execution plans、LangSmith のデータに合わせた custom storage layouts を追加していると説明されていた。
- `How we built it` では Engine が大量の production traces を扱い、multi-tenant orchestration と distributed task queue を通じて処理する構成が説明されていた。SmithDB はこのような trace / dataset / comparison の大規模処理を支える data layer 側の更新として位置づけられる。

参考:

- https://docs.langchain.com/langsmith/self-hosted-changelog
- https://x.com/andrewlamb1111/status/2054666729456812150?s=20
- https://datafusion.apache.org/
- https://datafusion.apache.org/user-guide/introduction.html
- https://vortex.dev/

### 3. Sandboxes

LangSmith Sandboxes は、agent が生成・実行するコードを安全に動かすための ephemeral で locked-down な実行環境。LLM に任意コードを実行させる場合、local machine や本番 infrastructure に直接触らせるのは危険なので、sandbox 側で filesystem、network、resource usage、実行可能 binary などを制御する。LangSmith SDK から利用でき、LangSmith Deployment や Deep Agents とも統合される。

ポイント:

- agent-generated code を隔離環境で実行
- CPU / memory / disk などの resource limits を管理
- binary authorization で実行可能な program や到達可能 domain を制限
- coding assistant、CI-style agent、data analysis agent などに有効

セッション補足:

- `Day1 keynote` では LangSmith Sandboxes の一般提供が発表され、agent が code を読み書き・実行して data manipulation や CLI 操作を行うための重要な execution environment として紹介された。
- sandbox は 1 秒未満で起動でき、interaction をまたいだ persistence、snapshot / restore、auth proxy を備えると説明されていた。
- `Introducing Managed Deep Agents` では、研究 agent であっても統計処理や report への反映などで code execution が必要になり、ほぼすべての agent が coding-agent 的な能力を必要としつつある、という文脈で Sandboxes が説明された。
- sandbox credential injection は agent 本体や sandbox environment に重要な environment variables を露出させないための機能として触れられていた。

参考:

- https://www.langchain.com/blog/introducing-langsmith-sandboxes-secure-code-execution-for-agents

### 4. Managed Deep Agents

Managed Deep Agents に相当する発表として、LangChain は `deepagents deploy` を beta として紹介している。これは Deep Agents harness を production-ready な server として立ち上げる仕組みで、model、instructions、tools、skills、sandboxes をまとめてデプロイできる。Claude Managed Agents との比較では、Deep Agents は open source / model-agnostic で、memory を標準形式で所有・照会できる点が強調されている。

ポイント:

- `deepagents deploy` で Deep Agents harness を production server 化
- model、`AGENTS.md`、skills、MCP tools、sandbox をまとめて指定
- horizontally scalable な server として運用する前提
- proprietary harness に memory を lock-in しない設計

セッション補足:

- `Introducing Managed Deep Agents` では、Managed Deep Agents は private beta として紹介され、prototype / working agent を production に持っていくためのまとめ役として説明されていた。
- 構成要素は大きく、Deep Agents harness、production runtime、Context Hub integration、Sandboxes の 4 本柱として説明されていた。
- runtime は LangSmith Deployment 上に構築され、agent の create / update / invoke、horizontal scaling、durable checkpoint、resume / replay、human-in-the-loop を支える。
- production では inbound user auth、agent から外部サービスへの outbound auth、agent の作成・更新権限、interoperability が重要になる、という運用面の話も補足されていた。

参考:

- https://www.langchain.com/blog/deep-agents-deploy-an-open-alternative-to-claude-managed-agents
- https://www.langchain.com/blog/april-2026-langchain-newsletter

### 5. LLM Gateway

LLM Gateway について、LangChain 公式 docs では LangSmith の LLM auth proxy が関連機能として確認できる。これは LangSmith と upstream LLM provider / internal gateway の間に置く Envoy-based component で、LangSmith からの model invocation に対して organization 側の認証・credential injection・request / response transformation を適用する。provider key を end user に露出せず、request を actor に traceable にするための enterprise 向け機能。

ポイント:

- LangSmith と OpenAI / Anthropic / internal LLM gateway などの間に配置
- LangSmith-signed JWT を検証し、組織側の認証フローを適用
- provider credentials を end user に露出せずに注入
- OpenAI format と custom gateway format 間の変換にも利用可能

セッション補足:

- `Day1 keynote` と `Introducing Managed Deep Agents` では、auth proxy が sandbox / agent 実行環境の外側に置かれ、agent が API を使う必要がある場合でも credential を agent や sandbox に直接見せずに traffic へ注入する仕組みとして説明されていた。
- Managed Deep Agents の production 説明では、外部 services / MCP tools へ outbound で接続するときに、正しい permission を仮定して安全に認証することが重要だと強調されていた。LLM Gateway / auth proxy はこの production auth layer の一部として捉えられる。

参考:

- https://docs.langchain.com/langsmith/llm-auth-proxy-self-hosted

### 6. Context Hub

Context Hub は、production agent が使う instructions や tools を version-controlled / environment-aware に管理する LangSmith の機能。context は agent または skill の versioned bundle として扱われ、`AGENTS.md` や `SKILL.md`、tools などを commit history つきで管理できる。staging / production への promote により、agent が pull する context を安定化できる。

ポイント:

- agent / skill の instructions と tools を versioned bundle として管理
- commit history により差分確認・rollback・tagging が可能
- staging / production へ promote して環境ごとの context を固定
- reusable skill を複数 agent から参照できる

セッション補足:

- `Day1 keynote` では LangSmith Context Hub の launch が発表され、agents files、skills、社内 wiki のような markdown knowledge をまとめて保存・配布する場所として紹介された。
- Context Hub では versioning、tags、comments が使え、local に pull して coding CLI で使ったり、Deep Agents の virtual filesystem として使ったりできると説明されていた。
- context は prompts から、AGENTS.md や skills のようなより構造化された instructions / capabilities へ進化している、という流れで説明されていた。
- `Introducing Managed Deep Agents` では、Context Hub integration が Managed Deep Agents の中核の 1 つとされ、agent が実際に動くための `AGENTS.md` や skills を versioning し、staging / production へ promotion できる仕組みとして触れられていた。

参考:

- https://docs.langchain.com/langsmith/use-the-context-hub
- https://docs.langchain.com/langsmith/context-engineering-concepts

### 7. Deep Agents 0.6

Deep Agents は、長時間・複雑な task を扱う agent harness。LangChain blog では初期設計として planning tool、filesystem access、subagents、detailed prompts が核だと説明されており、0.2 では pluggable backend / composite backend による memory・filesystem 拡張が紹介された。PyPI release history では `deepagents` 0.6.0 が 2026年5月12日に公開され、翌日に 0.6.1 も公開されている。公式ブログで 0.6 専用の詳細記事は見つからなかったため、ここでは Deep Agents の方向性と release 状況を記録する。

ポイント:

- planning tool、filesystem、subagents、detailed prompts を備えた agent harness
- pluggable backend により local filesystem、LangGraph Store、長期 memory などを扱いやすくする方向
- Open models を Deep Agents SDK で利用する記事も公開され、model-agnostic な harness としての位置づけが強い
- `deepagents` 0.6.0 は 2026年5月12日に PyPI で公開

セッション補足:

- `Day1 keynote` では Deep Agents 0.6 の発表として、open models、execution environment、streaming の 3 つの流れに対応する更新だと説明されていた。
- open source / open weight models の性能向上と cost pressure を背景に、Deep Agents 0.6 は open models を試しやすくする方向に進んでいる。
- execution environment では、full sandbox と virtual filesystem の中間に位置する code interpreter が紹介されていた。QuickJS を使い、agent が JavaScript を書いて実行し、tools の programmatic call や data file の操作を行える lightweight な実行環境として説明されていた。
- streaming では新しい streaming protocol と複数の frontend SDK、CopilotKit / assistant-ui / Vercel などの UI framework との統合が紹介され、agent UI を作りやすくする方向性が示されていた。
- `Introducing Managed Deep Agents` では、Deep Agents の基本能力として execution environment、context management、delegation、steering / human-in-the-loop が整理されていた。特に subagents は isolated context で動き、main agent の context を汚さずに並列化できる点が強調されていた。

参考:

- https://www.langchain.com/blog/doubling-down-on-deepagents
- https://www.langchain.com/blog/open-models-have-crossed-a-threshold
- https://www.langchain.com/blog/how-we-built-langchains-gtm-agent
- https://pypi.org/project/deepagents/
