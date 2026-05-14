# How We Built It

- 日付: 2026年5月13日
- 時間: 2:20 PM-2:40 PM
- 登壇者: Ben Tannyhill, Vivek Trivedy
- 音声: [How we built it.m4a](How%20we%20built%20it.m4a)
- 文字起こし: [How we built it_original.txt](How%20we%20built%20it_original.txt)

## 要約

このセッションでは、LangSmith Engine がどのように作られたか、また Engine を評価・改善するためにどのような設計判断があったかが説明された。LangSmith team は内部で go-to-market agent など多数の agents を運用しており、production traces を見ながら改善しても、小さな bugs / regressions / unsatisfactory responses が繰り返し発生するという課題を抱えていた。

Engine の目的は、production traces から issue を自動検出し、修正案を作り、再発防止の eval / dataset example まで生成すること。UI では prioritized inbox として issues を表示し、offending traces、prompt / agent file の変更案、GitHub PR、custom online evaluator、offline eval 用の ground truth examples をつなげる。

初期版 Engine は traces を coding agent に渡して PR を作る GitHub Action 的な仕組みから始まった。実際に silent tool failure を修正したり、internal coding agent の missing functionality を追加する PR を作ったりしたが、同時に「問題ではないものまで問題として見つけすぎる」という課題もあった。そのため、重要で意味のある issue を見つけ、actionable な単位に蒸留することが最重要設計課題になった。

architecture では、Engine は schedule または manual trigger で起動し、multi-tenant orchestration / distributed task queue / LangSmith Deployment / Deep Agents / Sandboxes を使う。trace は condensed / summarized version を入力にし、必要に応じて深掘りする。source code も optional に接続され、diagnosis と PR generation に使われる。

評価面では、Engine 自体にも eval が必要だと説明された。internal traces、synthetic data、human review、targeted tasks、representative traces を使い、issue identification、fix generation、eval creation を測る。さらに、Engine の traces を別の Engine に戻して改善する self-improving loop の可能性にも触れられた。

## 重要ポイント

- Engine は production traces から issue / fix / eval / dataset をつなぐ self-healing loop。
- 最初の難所は、意味のある issue を actionable に見つけること。
- traces は Engine にとって最重要入力で、source code は診断と PR 作成を補助する。
- Engine は Deep Agents、Sandboxes、LangSmith Deployment など複数の LangChain 製品で構成される。
- 顧客ごとに重要な issue は異なるため、feedback / memory file 的な preferences が必要。
- Engine 自体も eval-driven に改善され、将来的には Engine が Engine を改善する loop が見込まれる。
