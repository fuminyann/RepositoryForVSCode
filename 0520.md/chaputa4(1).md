1. 複数画面（ページ）を使う理由
アプリが複雑になると、一画面では収まらない

ログイン → ホーム画面、設定画面、詳細画面など

Flutterでは画面 = Widgetとして作り、ルート（道順）で切り替えるのが基本

🔸2. Navigatorウィジェットの概要
Flutterでは、画面の切り替えに Navigator という機能を使います。

ページのスタック管理（後から追加、前に戻るなど）

スマホアプリでよくある戻るボタン操作も含めて制御可能

🔸3. 画面を切り替える方法（Navigator.push）
dart
コピーする
編集する
Navigator.push(
  context,
  MaterialPageRoute(builder: (context) => 次の画面()),
);
MaterialPageRoute を使うことで、画面遷移がマテリアル風になる

新しい画面はウィジェットで作る（例：SecondPage()）

🔸4. 戻る処理（Navigator.pop）
画面を戻すときは Navigator.pop(context) を使う。

dart
コピーする
編集する
ElevatedButton(
  onPressed: () {
    Navigator.pop(context);
  },
  child: Text('戻る'),
)
📌 iOSやAndroidの「戻るボタン」とも連動している。

🔸5. 別ファイルに分けて画面を管理する方法
画面ごとにウィジェットクラスを分けるのが良い設計

ファイルも分けることで、コードが読みやすく、管理しやすくなる

dart
コピーする
編集する
// main.dart
Navigator.push(
  context,
  MaterialPageRoute(builder: (context) => SecondPage()),
);

// second_page.dart
class SecondPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(...);
  }
}