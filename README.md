### タイムラインをハッシュタグで検索して、「いいね」してみる

もちろん、「yaylib」では情報を取得するだけでなく、アクションを実行することもできます。

以下のコードでは、「いいねでレター」というハッシュタグがついた投稿を取得し、「いいね」します。

先程のコードと違うのは、最初に**ログインする必要がある**ことです。

![image](https://github.com/qvcoz/testing/assets/132273317/051673cc-9ed7-4fda-ba55-849d3fd9e2b1)

Replitでは、メールアドレスとパスワードを安全に保護するために「Secrets」という機能を使いましょう。

「Secrets」を使用することで悪意のある外部の人がログイン情報を閲覧するのを防ぎます。

![image](https://github.com/qvcoz/testing/assets/132273317/a477d673-e0c1-4a15-a30d-97c25ccb2819)

メールアドレスやパスワードはここに記入し、ソースコードからインポートします。

![image](https://github.com/qvcoz/testing/assets/132273317/3cafbb1c-1c31-4e75-9ef0-29e52733c020)


「2023-06-25...」と赤く表示されているところが、「いいね」のアクションの実行結果です。

スマホのアプリなどでログインしてみると、いいねできていることが確認できます。

※ コピペ用のコード

```python
import os
import yaylib

email = os.environ['email'] # メールアドレスをインポート
password = os.environ['password'] # パスワードをインポート

api = yaylib.Client() # yaylibを使う前のおまじない（yaylibの初期設定）
api.login(email, password) # ログイン

timeline = api.get_timeline_by_hashtag('いいねでレター') # 「いいねでレター」でハッシュタグを検索

for post in timeline.posts: # タイムラインの投稿を一つずつ取り出す
  print('投稿者の名前: ' + post.user.nickname)
  print('投稿本文: ' + post.text)

  api.like_posts(post.id) # 「いいね」する
```
