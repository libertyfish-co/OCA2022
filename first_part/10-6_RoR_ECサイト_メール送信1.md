## 10.6 Ruby on Rails：ECサイトの開発 メール送信1

### 10.6.1 メール送信のプロトコルの概要

メールを送信するためには、一般的にはSMTPを利用します。

SMTP(Simple Mail Transfer Protocol)の動作はおおよそ以下の流れになります。

- メールソフトやRailsがメールの送信者、受信者、タイトル、本文、添付ファイルなどのデータを組み立てます。
- メールソフトやRailsが組み立てたメールの情報を設定されているメールサーバに送信します。
- 送信側のメールサーバは、メールの送信者を認証してからメールを受け取ります。
- 送信側のメールサーバは、受け取ったメールの受信者のアカウントがある受信側のメールサーバに転送します。
- 受信側のメールサーバは、受け取ったメールの受信者がメールサーバに登録されているアカウントであるか確認し、有効であればアカウントのポストに保存します。

ここでは、送信しか取り扱いませんが、メールを受信するためには、一般的にはPOP(Post Office Protocol)もしくはIMAP(Internet Message Access Protocol)を利用します。

POPの動作はおおよそ以下の流れになります。

- メールソフトやRailsが設定されているメールサーバのポストに接続を要求します。
- メールサーバは要求されたアカウントとパスワードが有効であれば、ログインを許可します。
- メールサーバは要求してきたアカウントのポストに保存されているメールの件数やメールを返信します。

### 10.6.2 メール送信

ここでは、購入後にメールを送信する機能を実装していきます。
簡単にActionMailerについて説明し、Railsアプリケーションでのメール送信機能を実装します。

### 10.6.3 ActionMailerとは

ActionMailerとは、Railsのデフォルトのgemで、メールの送信や受信を行うことが可能となっています。
今回は、このActionMailerでのメール送信について説明していきます。
ActionMailerを使用することで、MailerクラスとViewでメールを送信することができます。
これは、今まで作成してきた画面でのControllerクラスとViewの関係に似ています。

なお、メールの送信や受信には、別途メールサーバが必要になります。

最終的に送信先にメールを配送するのはメールサーバの担当になります。この動作は、一般的なメールソフトの動作と同じです。

ActionMailerでは、送信するメールの形式としてHTML形式とテキスト形式が利用できますが、ここではHTML形式でメールを送信するよう実装します。
