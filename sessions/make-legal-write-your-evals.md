# Make Legal Write Your Evals

- 日付: 2026年5月13日
- 時間: 1:40 PM-2:00 PM
- 登壇者: Philipp Comans
- 関連ファイル名: chime _ make legal write your evals
- 音声: [chime _ make legal write your evals.m4a](chime%20_%20make%20legal%20write%20your%20evals.m4a)
- 文字起こし: [chime _ make legal write your evals_original.txt](chime%20_%20make%20legal%20write%20your%20evals_original.txt)

## 要約

Chime のセッションでは、規制産業における agent evals を legal / compliance team と共同で作る方法が紹介された。Chime の agent `Jake` は、members が smarter spending、saving、long-term financial growth を実現するための financial profile / assistant として説明された。金融領域では agent の「oops」が trust を壊すだけでなく regulator issue にもつながるため、compliance は中核要件になる。

従来の compliance review は、kickoff と release gate にだけ現れることが多く、engineers は途中で何を eval すべきかを推測するしかない。登壇者は、evals を alignment surface として使い、legal / compliance を継続的に開発プロセスへ参加させるべきだと説明した。

具体的には、legal / compliance が抽象的に語る risk を、domain、category、concrete risk へ分解する。たとえば compliance domain の中に consumer protection や unauthorized advice があり、その下に unauthorized tax advice、investment advice、legal advice などの concrete risks を置く。legal team は prohibited content、legal basis、allowed alternatives、example questions を自分たちの言葉で定義する。

その structured risk definition から dataset と LLM-as-judge evaluator prompt を生成し、rubric と pass / fail を測る。結果は taxonomy に沿って集計できるため、engineer は individual risk を見て改善し、compliance は category pass rate を見て sign-off し、executive は safety / compliance 全体の状態を見られる。

## 重要ポイント

- evals は legal / compliance との alignment surface になる。
- risk を domain / category / concrete risk に分解すると、双方が同じものを見られる。
- legal team は risk definition、prohibited content、allowed alternatives、example questions を書ける。
- structured risk definition から dataset と evaluator prompt を生成する。
- expert annotation は agent prompt、dataset generator、judge prompt、risk definition の改善に戻せる。
- 信頼は release gate で突然作るのではなく、開発中に evidence とともに積み上げる。
