# Building AI for Healthcare

- 日付: 2026年5月14日
- 時間: 2:00 PM-2:20 PM
- 登壇者: Janie Lee
- 音声: [Building AI for Healthcare.m4a](Building%20AI%20for%20Healthcare.m4a)
- 文字起こし: [Building AI for Healthcare_original.txt](Building%20AI%20for%20Healthcare_original.txt)

## 要約

このセッションは、Abridge による healthcare AI の事例だった。Abridge は clinical intelligence platform として、医師と患者の会話を臨床的に有用な chart note に変換するところから始まり、その後、会話データをもとに医療ワークフローを支援する agent system へ広げている。

healthcare は high-stakes / high-trust な領域であり、速度だけを優先することはできない。誤った note、誤った medication、誤った clinical interpretation は patient safety に直結する。また HIPAA や PHI の扱い、enterprise healthcare buyer が求める security / trust の水準も高い。このため、velocity と quality を両立するための evaluation、review、release process が重要になる。

セッションでは、最初の核となる note product と、そこから広がる agent system の2つのケースが扱われた。note product では、会話から正確で臨床的に使える chart note を作ることが価値の中心であり、misattribution や hallucination、missing information への対策が重要になる。agent system では、患者訪問の before / during / after にまたがって、医師が必要な情報を探したり、複数システムを横断したり、clinical decision support を受けたりする体験が目指されていた。

プロダクト設計では、AI が前面に出すぎず、clinician の work を背景で支えることが重視されていた。発表では「air conditioning」のように、常に存在して役立つが、必要なとき以外は意識させない体験が理想として語られていた。また、医師が control を持ち続けること、explicit / implicit feedback から改善すること、clinical quality、safety、adversarial testing、tool selection を評価することが重要な原則として挙げられた。

## 重要ポイント

- healthcare AI では velocity は重要だが、quality と trust を犠牲にできない。
- 医師と患者の会話は、notes、billing、claims、prior authorization、medication など downstream workflows の起点になる。
- PHI / HIPAA / patient safety が、設計・評価・運用の前提になる。
- agent は clinicians の before / during / after visit workflow を横断して支援する。
- AI は「air conditioning」のように背景で支援し、clinician の control を保つべき。
- evaluation では clinical accuracy、safety、edge cases、tool selection を明示的に見る必要がある。
