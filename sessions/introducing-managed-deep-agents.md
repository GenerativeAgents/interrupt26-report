# Introducing Managed Deep Agents

- 日付: 2026年5月13日
- 時間: 2:00 PM-2:20 PM
- 登壇者: Sydney Runkle, Victor Moreira
- 音声: [Introducing Managed Deep Agents.m4a](Introducing%20Managed%20Deep%20Agents.m4a)
- 文字起こし: [Introducing Managed Deep Agents_original.txt](Introducing%20Managed%20Deep%20Agents_original.txt)

## 要約

このセッションでは、Deep Agents harness の基本能力と、それを production に持ち込む Managed Deep Agents が紹介された。冒頭では、agent は model + tools だけではなく、model を real world へ接続する harness が必要だと説明された。harness の役割は、task に対して right context at the right time を与えること。

Deep Agents の主要能力は、execution environment、context management、delegation、steering / human-in-the-loop の 4 つ。execution environment は file system や sandbox / code interpreter を含み、agent が scratch file を書き、code を実行し、dynamic runtime で問題解決できるようにする。context management では、summarization、context offloading、prompt caching、skills、short / long-term memory などで long-running agent の context overflow を防ぐ。

delegation では planning tool と subagents が紹介された。subagents は isolated context で動き、main agent の context を汚さず、task を parallelize できる。steering では approval、edit、reject、response request などの human-in-the-loop decision pattern が紹介された。

後半では Managed Deep Agents の private beta が説明された。これは Deep Agents harness、LangSmith Deployment ベースの runtime、Context Hub integration、LangSmith Sandboxes をまとめ、agent creation / update / invoke、horizontal scaling、durable checkpoint / resume / replay、auth、MCP / A2A interoperability、context promotion、sandbox credential injection / snapshot restore を production-ready にするもの。

## 重要ポイント

- agent harness は model に right context と action environment を与える層。
- Deep Agents の核は execution environment、context management、delegation、steering。
- subagents は isolated context と parallelization に有効。
- Managed Deep Agents は Deep Agents を production runtime として提供する private beta。
- LangSmith Deployment により scaling、checkpoint、resume、human-in-the-loop を支える。
- Context Hub と LangSmith Sandboxes が Managed Deep Agents の重要な構成要素。
