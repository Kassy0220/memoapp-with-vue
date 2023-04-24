# todoapp-with-vue

todoapp-with-vue は、ブラウザ上で ToDo の登録、一覧、編集、削除を行うことができるアプリです。

## アプリの起動方法

まずは、アプリをローカルに取得してください。

```
git pull https://github.com/Kassy0220/memoapp-with-vue
```

次に、パッケージをインストールします。

```
npm install
```

以上でアプリを起動する準備が終わりました。

次のコマンドを実行して、アプリを起動します。

```
npm run dev
```

アプリ起動後次のように表示されるので、
`Local:`の後に続く URL をブラウザで開くと、アプリを使用することができます。

[![Image from Gyazo](https://i.gyazo.com/7b4b8bbfcea6412ce442f4a4544991af.png)](https://gyazo.com/7b4b8bbfcea6412ce442f4a4544991af)

## アプリの使用方法

todoapp-with-vue では、次の操作を行うことができます。

### ToDo の作成と一覧

テキストボックス内に ToDo 内容を入力し、新規作成ボタンを押すと、ToDo を作成することができます。

作成された ToDo は、`作成したToDo`欄にリストで表示されます。

[![Image from Gyazo](https://i.gyazo.com/a690e7dfe7f03f059229cac927e24ee7.gif)](https://gyazo.com/a690e7dfe7f03f059229cac927e24ee7)

テキストボックス内に何も入力していない状態で新規作成ボタンを押すと、ToDo を作成することはできません。

[![Image from Gyazo](https://i.gyazo.com/2b3cb56176d71473d58ae6905afddeb0.gif)](https://gyazo.com/2b3cb56176d71473d58ae6905afddeb0)

### ToDo の編集

作成した ToDo は、`編集`ボタンを押すと編集することができます。

テキストボックスと更新ボタンが表示されるので、
ToDo を編集し更新ボタンを押すと、ToDo が更新されます。

[![Image from Gyazo](https://i.gyazo.com/b2cb3500979e072c5255cdaa9dcbe6a1.gif)](https://gyazo.com/b2cb3500979e072c5255cdaa9dcbe6a1)

ToDo 作成時と同じく、ToDo の中身が空の状態で ToDo を更新することはできません。

[![Image from Gyazo](https://i.gyazo.com/4beb9049de1ae762c071b0feae6635e5.gif)](https://gyazo.com/4beb9049de1ae762c071b0feae6635e5)

### ToDo の削除

作成した ToDo は、`削除`ボタンを押すことで削除することができます。

[![Image from Gyazo](https://i.gyazo.com/711ced0d256a113edfc5c14706c64daa.gif)](https://gyazo.com/711ced0d256a113edfc5c14706c64daa)
