# Internet (インターネット)
---
## How Internet works?
<div align="center"><img src="https://raw.githubusercontent.com/kurab/grimoireduit/images/01.png"></div>

Device(デバイス):
- PC(ピーシー)
- Smart Phone(スマホ)
- Tablet(タブレット)

Browser(ブラウザー):
- IE(アイイー)
- Chrome(クローム)
- Firefox(ファイヤー・フォックス)

Services(サービス):
- SNS(エスエヌエス)
- Blog(ブログ)
- Search Engine(検索エンジン)
  - Google(グーグル)
  - Yahoo!(ヤフー)
  → ググる（Search by google)
- Chat tool(チャットツール)
  - ChatWork(チャットワーク)
  - Slack(スラック)

- etc.

## DNS
<div align="center"><img src="https://raw.githubusercontent.com/kurab/grimoireduit/images/02.png"></div>

DNS(ディーエヌエス)とは?
Domain Name System(ドメイン・ネーム・システム)の略。インターネットのアドレス帳のこと。

## hosts
<div align="center"><img src="https://raw.githubusercontent.com/kurab/grimoireduit/images/03.png"></div>

**Hosts(ホスツ)**ファイルとは、アドレス帳のことで、IP アドレスと呼び方を登録しておくと、設定した呼び方で、サーバーを呼び出すことができるようになる。個人の PC かサーバー上で設定する。

例えば、個人の開発環境は社内だけで分かれば良いので、Global な Name Server に登録する必要はなく（しない方が良く）、Hosts に設定するのが一般的である。

Mac(マック) や Ubuntu(ウブンチュ)などの Unix(ユニックス)/Linux(リナックス)系OSの場合は、/etc/hosts にあり、Windows の場合は、バージョンによって異なるが Windows/system32/drivers/etc/hosts などにある。
Hosts に記載がある場合は、Name Server より優先される。

## Index
- [Grimoire du IT](../../README.md)
- Internet (インターネット)
- [Development Process (開発工程)](../process/README.md)
- [Inside of Server (サーバーの中身)](../server/README.md)
- [Implementation (実装)](../implement/README.md)
- [Test (テスト)](../test/README.md)
- [Server & Security (サーバーとセキュリティ)](../security/README.md)
- [練習問題](../practice/README.md)
