# 【Yay!】ついに API が公開！投稿やいいねを自動化してみた！

こんにちは！ p と申します(^^)

皆さんは、Yay!の API が公開されたことをご存知ですか？

この API が公開されたことによって Yay!を自動化したり、ボットの開発ができるようになったので、実践も混じえて初心者にもわかりやすく解説していきます。

### そもそも API とは？

API とは、外部のアプリケーションが Yay!の機能やデータを利用できるようにする仕組みを指しています。 Yay!のサイトやアプリを利用せずとも、外部のアプリケーションを通じて、投稿する、タイムラインを取得する、いいねする、リツイートするなどの操作を行うことができます。

この Yay!の API を公開＆開発したのは前回の記事で紹介した、投稿から性格を診断してくれるボット「MindReader AI」の開発者である**毛の可能性**さんと、プログラマーの**Konn**さんです。

### API の使い方

Yay!の API を利用するには、「**yaylib**」というツールをインストールする必要があります。

以下が大まかなインストール手順です。

    1.    GitHub のアカウントを作成する（無料）

    2.    yaylib のプロジェクトをスターする

    3.    yaylib をインストールする

それぞれ順を追って解説します。

#### 1. GitHub のアカウントを作成する（無料）

GitHub とは世界中の様々なプログラムが集まる Web サービスです。

既に GitHub のアカウントを所持している方は、「<a href="2-yaylib-のプロジェクトをスターする">yaylib のプロジェクトをスターする</a>」に進んでください。

GitHub アカウントの登録方法は以下のリンクを参考にしてください。

<a href="https://reffect.co.jp/html/create_github_account_first_time/">
1分もかからない！5ステップでGitHubアカウント作成
</a>

#### 2. yaylib のプロジェクトをスターする

GitHub のアカウント登録が完了したら、以下のリンクから「yaylib」をスターします。

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

![スクリーンショット 2023-06-25 152306](https://github.com/qvcoz/testing/assets/132273317/94c17ad2-7cd4-4b6e-8edf-b062e2426e23)

![スクリーンショット 2023-06-25 151705](https://github.com/qvcoz/testing/assets/132273317/ee223421-ce6b-4d01-8dcd-599f498cb174)

![スクリーンショット 2023-06-25 153540](https://github.com/qvcoz/testing/assets/132273317/47598c9d-f1c8-4a91-be51-9b617ac4e743)

![スクリーンショット 2023-06-25 155501](https://github.com/qvcoz/testing/assets/132273317/b051efe4-89b5-49cf-9d64-08e9457a8a62)

![image](https://github.com/qvcoz/testing/assets/132273317/eab420a1-5e29-4774-9c40-978cff990c82)

![image](https://github.com/qvcoz/testing/assets/132273317/47c43514-0a83-45be-8a0e-a140664a075a)

![image](https://github.com/qvcoz/testing/assets/132273317/8cc766ab-4138-408e-8f16-269223e99a04)

![image](https://github.com/qvcoz/testing/assets/132273317/fb6b9cd9-6068-4cd6-8808-5444f5bc588a)

