# memoapp-with-vue

memoapp-with-vue は、ブラウザ上でメモの登録、一覧、編集、削除を行うことができるアプリです。

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

memoapp-with-vue では、次の操作を行うことができます。

### メモの作成と一覧

テキストボックス内にメモ内容を入力し、新規作成ボタンを押すと、メモを作成することができます。

作成されたメモは、`作成したメモ`欄にリストで表示されます。

[![Image from Gyazo](https://i.gyazo.com/f3e951590155fcb1750c79dcc41ea820.gif)](https://gyazo.com/f3e951590155fcb1750c79dcc41ea820)

テキストボックス内に何も入力していない状態で新規作成ボタンを押すと、メモを作成することはできません。

[![Image from Gyazo](https://i.gyazo.com/cfe9daff0c9615e7bc533434a9dfedb9.gif)](https://gyazo.com/cfe9daff0c9615e7bc533434a9dfedb9)

### メモの編集

作成したメモは、`編集`ボタンを押すと編集することができます。

テキストボックスと更新ボタンが表示されるので、
メモを編集し更新ボタンを押すと、メモが更新されます。

[![Image from Gyazo](https://i.gyazo.com/9a93c56a07c01fc3449efc1be190c4f1.gif)](https://gyazo.com/9a93c56a07c01fc3449efc1be190c4f1)

メモ作成時と同じく、メモの中身が空の状態でメモを更新することはできません。

[![Image from Gyazo](https://i.gyazo.com/57d52657ea37865a97573698cbb8c0ef.gif)](https://gyazo.com/57d52657ea37865a97573698cbb8c0ef)

### メモの削除

作成したメモは、`削除`ボタンを押すことで削除することができます。

[![Image from Gyazo](https://i.gyazo.com/ec448e67dabfdde1e2d34e731a7a450f.gif)](https://gyazo.com/ec448e67dabfdde1e2d34e731a7a450f)
