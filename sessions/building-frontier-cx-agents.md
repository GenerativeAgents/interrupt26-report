# Building Frontier CX Agents

- 日付: 2026年5月13日
- 時間: 10:30 AM-10:50 AM
- 登壇者: Carlos Pereira
- 関連ファイル名: Cisco
- 音声: [Cisco.m4a](Cisco.m4a)
- 文字起こし: [Cisco_original.txt](Cisco_original.txt)

## 要約

このセッションでは、agent observability に特化した新しいデータ基盤 SmithDB が紹介された。agent traces は従来の logs / metrics と違い、深くネストされ、payload が大きく、multi-turn / multimodal で、検索・フィルタ・ランダムアクセスの要件も独特である。登壇者は、weekly trace volume が 150 million を超え、単一顧客が 1 日に 50 TB の trace data を送った例にも触れ、従来のデータ基盤では interactive な observability 体験を維持しにくいと説明した。

SmithDB は、agent observability のために purpose-built された database として紹介された。object storage をバックエンドに使い、compute / storage separation、cluster manager による work distribution、Postgres metadata store、SSD / memory cache、file compaction / shaping service を組み合わせる。trace 内の個別 step への random access、full-text search、thread navigation、metadata / tag / time filtering などの access pattern に最適化されている。

実装面では、全体が Rust で書かれ、Apache DataFusion と Vortex を基盤にしていると説明された。その上に、trace search 向けの custom inverted index layout、custom query planning / execution plans、storage layout の最適化を追加している。セッションでは、従来比で 6x-15x 高速になったという性能改善も紹介された。

## 重要ポイント

- agent traces は巨大・深い・multimodal で、通常の logs / metrics とは異なる。
- SmithDB は LangSmith の trace observability 向けに作られたデータ基盤。
- object storage と compute / storage separation により scale と cost を両立。
- Apache DataFusion と Vortex を土台にし、Rust で実装。
- random access、full-text search、thread view、metadata filtering に最適化。
- SmithDB は LangSmith Engine など次の improvement loop の基盤にもなる。
