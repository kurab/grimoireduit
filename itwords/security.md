# Server & Security(サーバーとセキュリティ)
## 色々なサーバー
<div align="center"><img src="https://raw.githubusercontent.com/kurab/grimoireduit/images/10.png"></div>

例えば、普段は10くらいでそんなにアクセスがないけど、クリスマスシーズンはアクセスが100倍くらい増えるというようなサービスの場合…

オンプレの場合、クリスマスシーズンに対応できる分のサーバーを購入して、設置しておく必要がある。お金がかかるし、本当にそれで大丈夫か確証はない。
クラウドサーバーの場合、クリスマスシーズンのみ必要な分だけ増やして、普段は10にしておくということができる。無駄がない。


## 色々なアクセス方法
|Protocol<br>(プロトコル)|Default Port<br>(ポート)|用途|関連用語|
|:-:|:-:|:-:|:-:|
|**http**<br>(エイチティティピー)|80|通常のブラウザアクセスなど||
|**https**<br>(エイチティティピーエス)|443|個人情報等を送信する時に暗号化する|**SSL**(エスエスエル)<br>SSL通信, SSL証明書|
|**FTP**<br>(エフティピー)|20,21|ファイルをアップロード・ダウンロードする||
|**ssh**<br>(エスエスエイチ)|22|サーバに入って色々やる|**Command Line**<br>(コマンドライン)<br>(**cmd, cli**)|
|**SMTP**<br>(エスエムティピー)|23|メール||

サーバーとの通信方法の種類のことをプロトコルと呼ぶ。サーバーはプロトコルごとに番号で指定された入り口を持っており、それをポートと呼ぶ。ssh 通信のことを22番通信と呼んだりもする。サーバー管理者は必要に応じて、ポートを開いたり閉じたり、番号を変えたりする。不用意に開いていると、いたずらされたり、ドロボウが入ってくる。通信の制限のことを、**Fire Wall(ファイヤーウォール)**と呼ぶ。

通常はサービス単位でFire wallを設定するが、例えば中国の Great Fire Wall(グレートファイヤーウォール)のような、Facebook や Twitter などの SNS への通信を国として制限している場合もある。


## Fire Wall
<div align="center"><img src="https://raw.githubusercontent.com/kurab/grimoireduit/images/11.png"></div>

Fire Wall は特定の相手からの通信を遮断したり、特定の相手からの通信だけを許可したりします。


## Proxy
<div align="center"><img src="https://raw.githubusercontent.com/kurab/grimoireduit/images/12.png"></div>

Fire Wall に通信をはじかれてしまう場合、別人になりすましてアクセスすることがあります。別人になりすますことを **Proxy(プロクシー)を通す**とか **Proxy をさす**とか表現します。（プロクシー → 串 → 刺す）


## NAT(ナット)
<div align="center"><img src="https://raw.githubusercontent.com/kurab/grimoireduit/images/13.png"></div>

個別に直接通信するのではなく、**NAT**(~~Nguyen Anh Tuan~~ Network Address Transfer)サーバーを介して通信するようにすることで、セキュリティを向上させることができます。**Bastion**(バッション/踏み台)サーバーと呼ぶこともあります。
ssh 通信を Bastion サーバー経由で行うことを**多段ssh**(ただんエスエスエイチ), **ssh tunnel**(エスエスエイチ・トンネル), **Port forward**(ポート・フォワード)などという言葉を使って表現します。
NAT サーバーを経由する設定のことを **Route Table**(ルートテーブル)と呼びます。

セキュリティ目的ではありませんが、http/https のリクエストを一括で受けて、それぞれの Web サーバーに振り分ける目的で Proxy サーバーを設置することもあります。先程の Proxy との違いは、ユーザー側ではなく、サーバー側がなりすます点です。


## Subnet(サブネット)
<div align="center"><img src="https://raw.githubusercontent.com/kurab/grimoireduit/images/14.png"></div>

**Subnet(サブネット)**とは、Network を小分けにしたものです。セキュリティのためであったり、役割のためであったりグルーピングしてあった方が何かと便利なことがあるので、Subnet に分割します（本来の目的は違うけどいまは省略）。IP Address はインターネット上の住所ですが、フロアくらいに思っておくと良いかも知れません。会社の受付があったり来客用スペースがある Public なフロア、従業員が業務を行う Private なフロアなど。

IP Address 的には、以下のようになります。
<div align="center"><img src="https://raw.githubusercontent.com/kurab/grimoireduit/images/15.png"></div>


## NACL & SG
<div align="center"><img src="https://raw.githubusercontent.com/kurab/grimoireduit/images/16.png"></div>

Subnet に設定するセキュリティ設定のことを **Network ACL**(ネットワークエーシーエル)とか、**NACL**(ナクル)と呼びます。Network Access Control Lists の略です。NACL では大雑把に許可する通信を設定します。
個別のサーバーにはそれぞれ個別に細かくセキュリティの設定をします。利用しない Port を開けておくのは危ないので、必要な Port だけを開けるように設定します。その設定は使い回しができるので、**Security Group**(セキュリティグループ)と呼ばれています。

NACL と SG では、入ってくるものと出て行くものに分けて設定を行います。入ってくるものを **Inbound**(インバウンド), 出ていくものを **Outbound** (アウトバウンド)と呼びます。


## Availability Zone(アベイラビリティゾーン)
<div align="center"><img src="https://raw.githubusercontent.com/kurab/grimoireduit/images/17.png"></div>

全部同じところに置いておくと、何か問題が発生した時に困るので、別のところにバックアップを作り、手動/自動で切り替えます。
AWS では、大きく分けて **Region**(リージョン)と**Availability Zone**(アベイラビリティ・ゾーン、AZ)の2種類の Zoning の考え方があります。Region は Tokyo とか Oregon とかサーバーが置いてある場所が全然違います。AZ は、同じ Region 内にありますが、それぞれがなるべく影響しないように設置されています。
Region ごとに提供されるサービスが異なります。

AWS で現在(1/12/2017)提供されているリージョンは、
North Virginia, Ohio, North Carolina, Oregon, Canada, Ireland, Frankfurt, London, Tokyo, Seoul, Singapore, Sydney, Mumbai, San Paulo で、最近中国から AWS は撤退・パートナー企業に譲渡されたので、Beijing Region は AWS としてのサービスからは外れました。


## Load Balancer(ロードバランサー)
<div align="center"><img src="https://raw.githubusercontent.com/kurab/grimoireduit/images/18.png"></div>

一度にたくさんのアクセスがあった場合、1台のサーバーでは処理しきれなくなることがあります。その場合、同じ構成のサーバーを用意しておいて、リクエストを分散させて処理を行います。負荷分散と呼び、それを行うものを Load Balancer(ロードバランサー)と呼びます。AWS では、**ELB(イーエルビー/Elastic Load Balancer)** とか **ALB(エーエルビー/Application Load Balancer)**と呼ばれています。ALB は ELB の新しいバージョンなので、今後 ELB を積極的に選択する理由はあまりありませんが、AWS の LB は古くから ELB と呼ばれてきたので、ALB もひっくるめて ELB と呼ぶことが多い気がします。

オンプレミスの場合、たくさんのアクセスを想定し、サーバーを用意する必要がありますが、クラウドの場合、必要に応じて増やすことができます。サーバーを増やすことを **Scale out(スケールアウト)**と言い、ELB の機能で、ある一定の条件を超えたら自動で増やす **Auto Scaling(オートスケーリング)**というものがあり、お財布に優しくなっています。Auto Scaling はサーバー郡に対して設定できます(Auto Scaling Group)。

一方で、サーバーの容量や処理能力自体を増強して処理を行う場合もあり、これを **Scale Up(スケールアップ)**と呼びます。


## 色々なサーバー
|タイプ|用途|例|メモ|
|:-:|:-:|:-:|:-|
|**EC2**<br>(イーシーツー/Elastic Compute Cloud)|いわゆる普通のサーバー||**AMI**(エーエムアイ/Amazon Machin Image)から簡単に立ち上げられる|
|**RDS**<br>(アールディーエス/Relational Database Service)|データベース|Oracle, MySQL, PostgreSQL<br>(オラクル, マイエスキューエル, ポスグレ)||
|**ElastiCache**<br>(エラスティキャッシュ)|KVS(ケーブイエス/Key Value Store)<br>キャッシュ|**Redis, Memcache**<br>(レディス, メムキャッシュ)|On Memory(オンメモリー)のキャッシュ。アクセスが速い。|
|**S3**<br>(エススリー/Simple Storage Service)|File Storage<br>(ファイルストレージ)<br>ファイル置き場||S3の中に**Bucket**(バケット)と呼ばれる容れ物を作って使う|
|**NoSQL**<br>(ノーエスキューエル)|データベース|**MongoDB**<br>(モンゴデービー)|||

それぞれのサーバー1台1台のことを**Instance**(インスタンス)と呼び(EC2インスタンスとか)、インスタンスごとにスペックを設定する。Small とか Large とか。


## AWS のその他のサービス
|サービス名|用途|メモ|
|:-:|:-:|:-|
|**SES**<br>(エスイーエス/Simple Email Service)|メール送信|オレゴンかバージニア。<br>EC2インスタンス内に、SendMail(センドメール)やPostfix(ポストフィックス)を建てても良い|
|**KMS**<br>(ケーエムエス/Key Management Service)|暗号化キー||
|**IAM**<br>(アイアム/Identity and Access Management)|アカウント|個別リソースへの権限設定をする。個別のアカウントの他、**IAM Role** と呼ばれるサーバーに付与するものもある設置する|
|**Code Commit**<br>(コードコミット)|バージョン管理|ソースコードのバージョン管理ができる。IAM が必要。|
|**VPC**<br>(ブイピーシー/Virtual Private Cloud)|サーバー群をひとまとめにする括りのこと|VPC 同士を接続することを **Peer Connect**(ピアコネクト)と言う。同一 Region 内で Private IP が被らない場合に接続できる|
など


## Distribution Tool(ディストリビューションツール)
同じことをいちいち設定するのが面倒なので、設定ファイルを書いてコマンド等を実行して簡単に再現できるようにする**構成管理ツール**のこと。設定の(半)自動配信。

VPC 全体の設定(ネットワーク設定など)を再現する場合は、**CloudFormation**(クラウドフォーメーション),
個別サーバーの設定(インストールやアプリケーション設定、ソースコード配置など)は、**Ansible**(アンシブル)や**Chef**(シェフ・チェフ)などを利用するのが一般的。

基本的には、**xml**(エックスエムエル) や **yml**(ヤムル・ワイエムエル), json(ジェイソン) 等に設定を書く。**Template**(テンプレート)と言ったり、**Playbook**(プレイブック)と言ったり、**Cookbook, recipe**(クックブック, レシピ)と言ったりする。


## よく耳にするコマンド
|コマンド名|用途|メモ|
|:-:|:-:|:-|
|**yum**<br>(ユム・ヤム)|インストールに使う|**rpm**(アールピーエム), **apt, apt-get**(アプト, エーピーティ) など色々<br>ソースコードからインストールする場合は、**configure**(コンフィギュア)して、**make**(メイク)する|
|**grep**<br>(グレップ)|文字列検索||
|**nc**<br>(エヌシー, ネットキャット)|ネットワークの疎通確認に使う|相手のPortを指定して通信できるか調べる|
|**sudo**<br>(スドゥ, スドー)|**root**(ルート) ユーザとして実行する|SuperUserDo|
その他に、AWS 専用のコマンド aws-cli などをインストールして使ったりすることもある。
コマンド名が、ちょっと頭おかしい感じなのは、きっと当時作った人が疲れてたからに違いない。


## Index
- [Grimoire du IT](../itwords.md)
- [Internet (インターネット)](./internet.md)
- [Development Process (開発工程)](./process.md)
- [Inside of Server (サーバーの中身)](./server.md)
- [Implementation (実装)](./implement.md)
- [Test (テスト)](./test.md)
- Server & Security (サーバーとセキュリティ)
- [練習問題](./practice.md)

---
title: "Server & Security(サーバーとセキュリティ)"
title_sfx: "Grimoire du IT ~ IT 魔導の書"
date: "2018/07/27"
author: "kura"
breadcrumbs:
- name: "Home"
  url: "/"
- name: "Grimoire du IT ~ IT 魔導の書"
  url: "/articles/itwords"
- name: "Server & Security(サーバーとセキュリティ)"
---
