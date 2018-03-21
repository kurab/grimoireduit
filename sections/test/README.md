# Test(テスト)
---
## 色々なテスト
Test には色々な種類がある。大雑把に言えば、**Unit Test**(単体テスト)→**Integration Test**(結合テスト)→**System Test** (システムテスト)→**Acceptance Test**(受け入れテスト) の順番で行われる。

まずは、要求を分析し、どのような **Test View Point**(テスト観点)でテストすべきかを考え、スケジュールに落とし込む **Test Planning**(テスト計画)を行う。Test View Point には、機能要件のテストだけでなく、**非機能要件**のテストもあり、例えば、**Performance Test**(パフォーマンステスト), **Security Test**(セキュリティテスト/脆弱性テスト)などがある。
要求に基づき、**Test Spec/Test Case**(テスト仕様書)を作成し、テストを実施する。

Test の中には、他の機能に影響が出ていないかを調べる **Regression Test**(リグレッションテスト, 回帰テスト)や、ざっと確認する **Smoke Test**(スモークテスト), 一通り機能を使ってみる **Walkthrough Test**(ウォークスルーテスト), 特別情報を与えずユーザーとして使ってみる **Monkey Test**(モンキーテスト)など色々なものがあり、必要に応じて使い分ける。

**ISTQB**(アイエスティキュービー, International Software Testing Qualification Boards)という団体があり、資格を発行している。テストにおいて国際的に通じる共通言語として大変有益であり、LFTV においては、QA としての採用は ISTQB Foundation の資格を必須とし、何となくテストしないようにしている。

<div align="center"><img src="https://raw.githubusercontent.com/kurab/grimoireduit/images/08.png"></div>

|Test|何？|誰がやる？|
|:-:|:-:|:-:|
|Unit Test<br>(ユニットテスト/単体テスト, UT)|関数やメソッド等の小さい単位での正しく動作するかのテスト。開発者がテストコードを書く。<br>網羅率のことを Coverage(カバレッジ)と言う。|Developer|
|Integration Test<br>(インテグレーションテスト/結合テスト)|開発した機能が全体として正しく動作するかを検証する。|QA|
|System Test<br>(システムテスト)|本番環境とほぼ同じ環境で、全体として正しく動作するかを検証する。|QA|
|User Acceptance Test<br>(アクセプタンステスト/受け入れテスト, UAT)|発注者の本来の目的・意図通りに動作しているかを発注者が検証する|Customer|

## Automation Test(自動テスト)
<div align="center"><img src="https://raw.githubusercontent.com/kurab/grimoireduit/images/09.png"></div>

何度もやるテストは自動化すべきである。CI/CD の観点からも自動化を積極的に進めるべき。

**Jenkins**(ジェンキンス)が git のリポジトリのイベント(push など)を **Webhook**(ウェブフック)などで監視し、静的コード解析や UT, **Selenium** (セレニウム)による UI の自動テスト, Jmeter(ジェイメーター) や **Apache Bench**(アパッチベンチ)などによるパフォーマンステストなどなどを行い、**ChatWork** や **Slack** といったチャットツールにフィードバックする。などの構成が例として挙げられる。

どこまでやるかは担保すべき品質の定義次第である。

github を利用する場合、多くのツールが Jenkins を介さなくても連携できるため、その点で github のバリューは高い。お値段も高い。

## Index
- [Grimoire du IT](../../README.md)
- [Internet (インターネット)](../internet/README.md)
- [Development Process (開発工程)](../process/README.md)
- [Inside of Server (サーバーの中身)](../server/README.md)
- [Implementation (実装)](../implement/README.md)
- Test (テスト)
- [Server & Security (サーバーとセキュリティ)](../security/README.md)
- [練習問題](../practice/README.md)
