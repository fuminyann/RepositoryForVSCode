🔸11. 入力フォームを使って画面間でデータをやり取り
TextField を使ってユーザー入力を受け取る

TextEditingController を使うと入力内容をコード内で扱える

dart
コピーする
編集する
final _controller = TextEditingController();

TextField(
  controller: _controller,
  decoration: InputDecoration(labelText: '名前を入力'),
)
🔸12. 入力 → 次画面で表示 → 戻るまでの流れを整理
ポイントとなる流れ：

TextField に入力された文字列を取得（_controller.text）

Navigator.push() で次の画面へ、文字列を引数として渡す

次の画面で引数を受け取り、画面に表示

Navigator.pop(context, 戻す値) で戻る

元の画面で .then() を使って戻ってきた値を受け取る

🔸13. ボタンでフォームの内容を画面遷移に使う
dart
コピーする
編集する
ElevatedButton(
  onPressed: () {
    Navigator.push(
      context,
      MaterialPageRoute(
        builder: (context) => SecondPage(name: _controller.text),
      ),
    ).then((value) {
      setState(() {
        _result = value;
      });
    });
  },
  child: Text('次へ'),
)
SecondPage で受け取った値を Text() で表示

戻る ボタンで入力結果を返す

🔸14. 戻り値を使って画面を更新する
戻ってきた値を setState() で扱うことで、UIに反映させられる。

dart
コピーする
編集する
String _result = '';

setState(() {
  _result = value; // SecondPage から戻った値
});
🔸15. 状態と画面遷移のまとめ（図解）
状態の管理は setState() によって画面内で変更

画面遷移は Navigator.push() / pop() を使って他画面へ移動

値の受け渡しは「コンストラクタ引数」「戻り値」としてやり取り

📌このページまでで、画面間の移動と値のやり取りという、Flutterアプリ構築の基本パターンがひと通り学べました。

