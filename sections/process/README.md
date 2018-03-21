# Development Process(開発工程)
---
## 開発工程の例
<div align="center"><img src="https://raw.githubusercontent.com/kurab/grimoireduit/images/04.png"></div>

## 色々な開発工程マネジメント
|Flow type|Methodology<br>(メソドロジー/手法)|考え方|
|:-:|:-:|:-|
|**Water fall**<br>(ウォーターフォール)|**PMBOK**(ピンボック)|プロセスごとに役割分担が決まっており、完了させたら、次へ次へと渡していく。仕様書が完璧な場合うまくいく。|
|**Agile**<br>(アジャイル)|**Scrum**(スクラム)<br>**Lean**(リーン)<br>**XP**: eXtrem Programming<br>(エックスピー)<br>**Kanban**<br>(カンバン)|細かくフィードバックを受けながら認識の齟齬がないように、より意味のあるプロダクトが作れるように進める。<br>日本は契約の文化である点と、発注側の負担が大きいのであまりやりたがらない。|

## Role(ロール/役割)
<div align="center"><img src="https://raw.githubusercontent.com/kurab/grimoireduit/images/05.png"></div>

|呼び方|役割|
|:-:|:-|
|PO: Product Owner<br>PM: Project Manager<br>(ピーオー/ピーエム)|プロジェクトの責任者。お客様であることがほとんど。お金を出す意思決定を出来る人でない場合は、注意が必要。|
|Scrum Master<br>(スクラムマスター)|Scrum(スクラム)でやる場合の PM みたいな人。PO/PMとの違いは人事権以外の意思決定権がないことなど。|
|Designer<br>(デザイナー)|デザインする人。日本では html, css まで書く場合が多い。html, css だけ各人は、Coder(コーダー)とよばれることがある。日本にだけある特殊な職種。|
|Developer<br>(デベロッパー)<br>Frontend Engineer<br>(フロントエンドエンジニア)|プログラムを各人。アプリケーションを作る。|
|Server side Engineer<br>(サーバーサイドエンジニア)<br>Infrastructure Engineer<br>(インフラエンジニア)<br>Network Engineer<br>(ネットワークエンジニア)|サーバの設定等をやる人。ベトナムにはあんまりいない。|
|Tester<br>(テスター)<br>QA: Quality Assurance<br>(キューエー)<br>QC: Quality Control<br>(キューシー)|テストしたり、テストを設計したり、プロダクトの品質を管理する人。|

## Keywords of Scrum(唐突にスクラムのキーワード)
|Keyword(キーワード)|Description(意味)|
|:-:|:-|
|practice<br>(プラクティス)|Scrum の中で行うイベント|
|planning<br>(プランニング)|計画|
|Sprint/Iteration<br>(スプリント/イテレーション)|開発期間全体を一定期間ごとに区切って開発をする区切りのこと|
|Daily Scrum/Daily Stand up<br>(デイリースクラム/デイリースタンドアップ)|朝会|
|Review<br>(レビュー)|プロダクトオーナーにデモを行い、フィードバックを受ける|
|Retrospective<br>(レトロスペクティブ)|プロセスの振り返り会。改善案を話し合う|
|Product Backlog<br>(プロダクトバックログ)|要件リスト。プロダクトオーナーが管理|
|Priority<br>(プライオリティ/優先順位)|優先順位。必ず優先順位順に作る。|
|Ticket<br>(チケット)|タスク管理ツールなどで管理されるタスク|
|Kanban/Scrum Board<br>(カンバン/スクラムボード)|タスクを可視化する表|
|Velocity<br>(ベロシティ)|チームの開発速度|
|Pair Programming<br>(ペアプロ)|スキルの共有等の目的で、<br>2人1組でプログラミングを行う。|
|CI/CD: Continuous Integration/Delivery<br>(シーアイ/シーディ)|継続してリリースするための仕組み化のことを言うことが多い|
