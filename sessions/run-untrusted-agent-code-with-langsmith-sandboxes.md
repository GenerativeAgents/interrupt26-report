# Run Untrusted Agent Code with LangSmith Sandboxes

- 日付: 2026年5月14日
- 時間: 11:30 AM-11:40 AM
- 登壇者: Mukil Loganathan
- 音声: [Run Untrusted Agent Code with LangSmith Sandboxes.m4a](Run%20Untrusted%20Agent%20Code%20with%20LangSmith%20Sandboxes.m4a)
- 文字起こし: [Run Untrusted Agent Code with LangSmith Sandboxes_original.txt](Run%20Untrusted%20Agent%20Code%20with%20LangSmith%20Sandboxes_original.txt)

## 要約

このセッションは、agent が生成した code をどのように安全に実行するかを扱っていた。coding agent の利用が広がるにつれ、agent は script を書き、package を入れ、data analysis を行い、browser / computer use を通じて検証まで行うようになっている。これは非常に強力だが、同時に untrusted code execution のリスクを増やす。

LangSmith Sandboxes は、agent が書いた code を local machine や production infrastructure から切り離して実行するための基盤として紹介された。単なる container では不十分で、network egress、credentials、filesystem persistence、long-running execution、snapshot / restore、parallel experimentation などを扱う必要がある。

特に重要なのは credential exposure の防止である。セッションでは、sandbox 内に secret を直接置くのではなく、network traffic を proxy 経由にし、必要な credential を proxy 側で扱う設計が説明されていた。これにより、prompt injection などで agent が不正な request を試みても、runtime 内に秘密情報を持たせずに済む。

また、agent の作業は長くなりがちで、途中で filesystem state を維持したいケースも多い。そのため、ephemeral worker ではなく、必要に応じて永続化・復元できる sandbox が必要になる。

## 重要ポイント

- agent は software engineering だけでなく、data analysis、security testing、browser automation でも code を書く。
- untrusted agent code を直接 local / production 環境で動かすのは危険。
- LangSmith Sandboxes は、隔離実行、network control、persistence、snapshot / restore を提供する。
- credentials は sandbox 内に置かず、proxy 経由で扱う設計が重要。
- long-running agents には、作業状態を維持し、後から再開できる実行環境が必要。
- 複数の仮説を同じ初期状態から並列に試す用途にも sandbox が使える。
