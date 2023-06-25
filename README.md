# 【Yay!】ついに API が公開！投稿やいいねを自動化してみた！

<div align="center">
    <a href="https://github.com/othneildrew/Best-README-Template">
        <img src="https://github.com/qvco/yaylib/assets/77382767/5265b956-55b7-466c-8cdb-cf0f3abed946" alt="Logo" height="300px">
    </a>
</div>

こんにちは！ p と申します(^^)

皆さんは、最近 Yay!の API が公開されたことをご存知ですか？

この API が公開されたことによって Yay!を自動化したり、ボットの開発ができるようになりました。

この記事では、API を使用して Yay!を自動化する方法をプログラミングが初心者にもわかりやすく解説していきます。

### そもそも API とは？

API とは、外部のアプリケーションが Yay!の機能やデータを利用できるようにする仕組みを指しています。 Yay!のサイトやアプリを利用せずとも、外部のアプリケーションを通じて、投稿する、タイムラインを取得する、いいねする、リツイートするなどの操作を行うことができます。

この Yay!の API を公開＆開発したのは前回の記事で紹介した、投稿から性格を診断してくれるボット「<a href="https://yay.space/user/5855987">MindReader AI</a>」の開発者である**毛の可能性**さんと、プログラマーの**Konn**さんです。

## API の使い方

Yay!の API を利用するには、「**yaylib**」というツールをインストールする必要があります。

以下が大まかなインストール手順です。

    1.    GitHub のアカウントを作成する（無料）

    2.    yaylib のプロジェクトをスターする

    3.    yaylib をインストールする

それぞれ順を追って解説します。

#### 1. GitHub のアカウントを作成する（無料）

GitHub とは世界中の様々なプログラムが集まる Web サービスです。

既に GitHub のアカウントを所持している方は、「<a href="#2-yaylib-のプロジェクトをスターする">yaylib のプロジェクトをスターする</a>」に進んでください。

GitHub アカウントの登録方法は、以下の記事を参考にしてください。

<a href="https://reffect.co.jp/html/create_github_account_first_time/">
1分もかからない！5ステップでGitHubアカウント作成
</a>

#### 2. yaylib のプロジェクトをスターする

GitHub のアカウント登録が完了したら、以下のリンクから「yaylib」をスターする必要があります。

https://github.com/qvco/yaylib

スターは画面上部の右上に星ボタン ⭐️ があるので、そこをクリックします。

![スターする画像](https://github.com/qvcoz/testing/assets/132273317/87555194-10cb-4e1f-ac7d-38d0e5547b69)

#### 3. yaylib をインストールする

これで準備が整ったので、さっそく「yaylib」をインストールしていきます。

今回の記事では、プログラミング初心者の方のことも考慮して、難しい環境構築をスキップできる「Repl」というブラウザベースのコーディングツールを使用して解説します。

replit の登録は以下のリンクから行ってください。

<a href="https://replit.com/">https://replit.com/</a>

登録が完了したらホーム画面の左上にある「Create Repl」というボタンをクリックします。

![スクリーンショット 2023-06-25 151427](https://github.com/qvcoz/testing/assets/132273317/ee7edcce-6673-4305-af93-1cb39071014e)

すると以下のようなメニューが出てくるので、言語は、① Python を選択し、「Create Repl」をクリックしてプロジェクトを作成します。

![スクリーンショット 2023-06-25 153540](https://github.com/qvcoz/testing/assets/132273317/2fcd9665-a975-408e-b9b5-113b9ff89ccd)

そうすると、以下のような画面になると思います。

![スクリーンショット 2023-06-25 152306](https://github.com/qvcoz/testing/assets/132273317/94c17ad2-7cd4-4b6e-8edf-b062e2426e23)

右側の黒い画面、「Shell」のタブで、`pip install yaylib` と入力して「yaylib」のインストールを開始します。

![スクリーンショット 2023-06-25 151705](https://github.com/qvcoz/testing/assets/132273317/ee223421-ce6b-4d01-8dcd-599f498cb174)

ズラーっと出てきた最後らへんの文字に「Successfully installed」と「yaylib」という文字が表示されていれば、インストール完了です。

![スクリーンショット 2023-06-25 155501](https://github.com/qvcoz/testing/assets/132273317/b051efe4-89b5-49cf-9d64-08e9457a8a62)

### Yay!のタイムラインをプログラムから取得してみる

「yaylib」を用いると、とても簡単なコードで Yay!を自動化することができます。

以下のコードでは Yay!のタイムラインを取得して投稿者の名前と、投稿本文を表示します。

![image](https://github.com/qvcoz/testing/assets/132273317/47c43514-0a83-45be-8a0e-a140664a075a)

右側の黒い画面、「Console」のタブで実行結果を見ることができます。

ちゃんとデータが取得できていますね！

※ コピペ用のコード

```python
import yaylib # yaylibを使用しますという宣言

api = yaylib.Client() # yaylibを使う前のおまじない（yaylibの初期設定）

timeline = api.get_timeline() # タイムラインを取得

for post in timeline.posts: # タイムラインの投稿を一つずつ取り出す
  print('投稿者の名前: ' + post.user.nickname)
  print('投稿本文: ' + post.text)
```

### タイムラインをハッシュタグで検索して、「いいね」してみる

もちろん、「yaylib」では情報を取得するだけでなく、アクションを実行することもできます。

以下のコードでは、「いいねでレター」というハッシュタグがついた投稿を取得し、「いいね」します。

![image](https://github.com/qvcoz/testing/assets/132273317/8cc766ab-4138-408e-8f16-269223e99a04)

「2023-06-25...」と赤く表示されているところが、「いいね」のアクションの実行結果です。

スマホのアプリなどでログインしてみると、いいねできていることが確認できます。

※ コピペ用のコード

```python
import yaylib # yaylibを使用しますという宣言

api = yaylib.Client() # yaylibを使う前のおまじない（yaylibの初期設定）
api.login(email="メールアドレス",
          password="パスワード") # ログイン

timeline = api.get_timeline_by_hashtag('いいねでレター') # 「いいねでレター」でハッシュタグを検索

for post in timeline.posts: # タイムラインの投稿を一つずつ取り出す
  print('投稿者の名前: ' + post.user.nickname)
  print('投稿本文: ' + post.text)

  api.like_posts(post.id) # 「いいね」する
```

### 自動投稿したり、ボットを作成する方法

これ以外にもたくさん紹介したいところですが、記事が非常に長くなってしまうので、今回の記事での紹介は以上とさせていただきます。

より詳しい機能機能の種類や内容は、「yaylib」の公式ドキュメントを参考にしてください。

<a href="https://github.com/qvco/yaylib/blob/main/docs/README.md">「yaylib」- 公式ドキュメント</a>

また、「yaylib」のDiscordサーバーに参加すると、使い方がわからない場合には質問したり、開発メンバーの一員として携わることもできるそうです。

<a href="https://discord.gg/MEuBfNtqRN">Discordサーバーに参加する</a>


## まとめ

以上が「yaylib」を使って、Yay!を自動化する方法の解説でした。

「yaylib」を使用する上で気をつけて頂きたい点としては、いいねやレターのやり過ぎや、タイムラインなどの膨大なデータの取得はサーバーに負荷がかかります。一般ユーザーが気持ちよく利用するためにも、そういったことはなるべく避けるようにしましょう。

また、仮にアカウントが Ban されてしまっても完全に自己責任でお願いします。

「yaylib」は、Yay!の全ての機能を網羅しているので、アイデアさえあれば、どんな面白いボットでも作れてしまいます。

これから Yay!というアプリがユーザーの手によって、どのように進化していくのかすごく楽しみですね！
