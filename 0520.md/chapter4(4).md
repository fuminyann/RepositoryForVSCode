🔸16. 複数の戻り値を扱う方法
pop() で渡す戻り値は任意の型でOK。

たとえば、Mapやクラスのインスタンスを返すことも可能。

dart
コピーする
編集する
Navigator.pop(context, {'name': '佐々木', 'age': 25});
then() の受け取り側で型をチェックして扱う。

🔸17. async / await を使った画面遷移の簡潔な書き方
then() の代わりに await で結果を受け取る方法。

dart
コピーする
編集する
final result = await Navigator.push(
  context,
  MaterialPageRoute(builder: (context) => SecondPage()),
);
setState(() {
  _result = result;
});
非同期処理なので、async キーワードが必要。

🔸18. 名前付きルートによる画面遷移
複数の画面を管理するときは名前付きルートを使うと便利。

dart
コピーする
編集する
// main.dart
MaterialApp(
  routes: {
    '/': (context) => HomePage(),
    '/second': (context) => SecondPage(),
  },
);

// 遷移時
Navigator.pushNamed(context, '/second');
🔸19. ルートに引数を渡す方法（名前付きルート）
arguments に値を渡す。

dart
コピーする
編集する
Navigator.pushNamed(
  context,
  '/second',
  arguments: '佐々木',
);

// 受け取る側
final args = ModalRoute.of(context)!.settings.arguments as String;
🔸20. Chapter 4のまとめと次章の導入
Flutterの画面遷移の基本は押さえられた

Navigator.push と pop の使い方

値の渡し方、戻り値の受け取り方

名前付きルートの活用で管理が楽に

次章は「状態管理の応用」へ進む

