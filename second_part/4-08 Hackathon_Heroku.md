# 4.8 ハッカソン( Herokuデプロイ )

## 4.8.1 Heroku の利用

開発したアプリケーションをHerokuへデプロイしましょう。
Herokuは、PaaS（Platform as a Service）と呼ばれるクラウドサービスで、
ローカルのターミナルから直接Gitコマンドでデプロイすることが可能です。

## 4.8.2 ポイント

### Herokuへデプロイできること

アプリケーションをHerokuにデプロイしましょう。

### Herokuについての理解を深め、正しく利用できること

Herokuへのアカウント登録、heroku CLIでアプリケーションを作成し、gitによるherokuデプロイを行いましょう。
また、ログの表示など、herokuの基本的な使い方の理解も深めましょう。

`コマンド例`

```
Herokuへログイン
$ heroku login

Herokuにアプリ作成
$ cd ~/myapp
$ heroku create

アプリケーションをデプロイ
$ git push heroku master

ログ表示
$ heroku logs -t
```

### デプロイ時の注意事項
デプロイがうまくいかない場合は、下記事項に注意してみましょう。
解決できない場合は、ログを確認して解決策を調べてみましょう。

- Gemfile.lockが存在するか
- GemfileでproductionのDBを記載しているか
- dbのmigrateは実行しているか

## 4.8.3 発展事項
### Heroku アドオン

Heroku には、アプリケーションに機能を追加・拡張するアドオンが用意されています。
アドオンには、アプリケーションのパフォーマンスを向上させるものや、運用をサポートするなど様々のものが提供されています。
アドオンについて調べ目的にあったアドオンがあれば導入を検討してみましょう。
