🔸6. 画面に値を渡す（引数つきの画面遷移）
別画面に値を渡したいときは、画面ウィジェットのコンストラクタに引数を用意する。

dart
コピーする
編集する
// 遷移元
Navigator.push(
  context,
  MaterialPageRoute(builder: (context) => SecondPage(name: '佐々木')),
);

// 遷移先（SecondPage）
class SecondPage extends StatelessWidget {
  final String name;
  SecondPage({required this.name});

  @override
  Widget build(BuildContext context) {
    return Text('こんにちは、$nameさん');
  }
}
🟩 ポイント：required を付けて、必須の引数であることを明示

🔸7. 画面から値を返す（戻り値を受け取る）
push() のあとに .then() を使って、戻り値を受け取ることができる。

dart
コピーする
編集する
Navigator.push(
  context,
  MaterialPageRoute(builder: (context) => SecondPage()),
).then((value) {
  print('戻ってきた値: $value');
});
🔸8. 遷移先で pop() で値を返す
戻るときに値を返すには、pop(context, 戻す値) を使う。

dart
コピーする
編集する
Navigator.pop(context, 'ありがとう');
➡️ これが then() の value に渡る。

🔸9. 画面遷移と状態管理の違い
状態管理	画面切り替え
同じ画面内で値を変更	setState() を使う
異なる画面に移動する	Navigator.push() を使う
戻る時に値を渡す	Navigator.pop(context, 値)

🔸10. 演習：名前を入力して次の画面に表示
目的：
画面Aで名前を入力 → 画面Bにその名前を表示 → 戻るボタンで完了

dart
コピーする
編集する
Navigator.push(
  context,
  MaterialPageRoute(builder: (context) => NamePage(name: _controller.text)),
);