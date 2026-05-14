# Building AI for Healthcare

- 日付: 2026年5月14日
- 時間: 2:00 PM-2:20 PM
- 登壇者: Janie Lee
- 音声: [Building AI for Healthcare.m4a](Building%20AI%20for%20Healthcare.m4a)
- 文字起こし: [Building AI for Healthcare_original.txt](Building%20AI%20for%20Healthcare_original.txt)

## 写真タイムライン

EXIF時刻はJST相当で記録されていたため、PDTへ変換して時系列に並べている。

![Building AI for Healthcare 14:05:48](../img/IMG_3863.JPG)

*14:05:48 PDT。セッション冒頭。Janie Lee 氏が登壇している場面。*

![Building AI for Healthcare 14:05:54](../img/IMG_3864.JPG)

*14:05:54 PDT。セッション冒頭のスライド。*

![Building AI for Healthcare 14:05:59](../img/IMG_3865.JPG)

*14:05:59 PDT。Abridge / healthcare AI の導入部分。*

![Building AI for Healthcare 14:06:08](../img/IMG_3866.JPG)

*14:06:08 PDT。clinical intelligence platform の背景説明。*

![Building AI for Healthcare 14:11:18](../img/IMG_3867.JPG)

*14:11:18 PDT。Notes を core product / wedge として位置づけ、misattribution、confabulation、redundancy などの問題に触れているスライド。*

![Building AI for Healthcare 14:12:29](../img/IMG_3868.JPG)

*14:12:29 PDT。notes / evaluation に関する説明。*

![Building AI for Healthcare 14:12:35](../img/IMG_3869.JPG)

*14:12:35 PDT。healthcare AI の evaluation / quality 管理に関するスライド。*

![Building AI for Healthcare 14:12:35](../img/IMG_3870.JPG)

*14:12:35 PDT。同時刻に撮影された別カット。*

![Building AI for Healthcare 14:13:31](../img/IMG_3871.JPG)

*14:13:31 PDT。clinical note / product workflow に関する説明。*

![Building AI for Healthcare 14:15:02](../img/IMG_3872.JPG)

*14:15:02 PDT。Good annotations are key to making this work。annotation quality と reviewer alignment の重要性。*

![Building AI for Healthcare 14:15:53](../img/IMG_3873.JPG)

*14:15:53 PDT。annotation / evaluation process の続き。*

![Building AI for Healthcare 14:17:42](../img/IMG_3874.JPG)

*14:17:42 PDT。healthcare agent の設計原則に関するスライド。*

![Building AI for Healthcare 14:18:07](../img/IMG_3875.JPG)

*14:18:07 PDT。clinician workflow と agent experience に関する説明。*

![Building AI for Healthcare 14:18:27](../img/IMG_3876.JPG)

*14:18:27 PDT。doctor / patient visit 前後の支援に関するスライド。*

![Building AI for Healthcare 14:19:20](../img/IMG_3877.jpeg)

*14:19:20 PDT。high-stakes な healthcare agent の運用・評価に関する説明。*

![Building AI for Healthcare 14:20:09](../img/IMG_3879.JPG)

*14:20:09 PDT。セッション終盤。evaluation と safety の論点。*

![Building AI for Healthcare 14:21:39](../img/IMG_3880.JPG)

*14:21:39 PDT。CDS の evals。clinical quality、clinical safety、boundary / adversary testing、tool selection などの評価観点。*

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
