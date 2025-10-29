```
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'たいとる',
      home: 内容,
    );
  }
}
```
# ウィジェットの種類
状態(ステート)の有無
- StatelessWidget
- StatefulWidget
# Text
```
Text(
    "からあげｱｱｱｱｱｱｱｱｱｱ",
    style: TextStyle(
        fontSize: サイズ,
        fontWeight: FontWeightクラス定数,
        color: Colorクラス,
        fontFamily: "フォント"
    )
)
```
# StatefulWidget / State
```
class ウィジェットクラス extends StatefulWidget{
    @override
    ステートクラス createState() => ステートクラス();
}

class ステートクラス extends State<ウィジェットクラス> {
    @override
    Widget build(BuildContext context){

    }
}
```
buildは更新の度に呼ばれる
# setState
ステートの更新をステートクラスに知らせる、描画を更新
```
setState((){
    変更
});
```
# Scaffold
土台
```
Scaffold(
    appBar: AppBar(
        title: Text('ばー'),
    ),
    body: 内容
)
```
# FloatingActionButton
右下に浮いたボタン  
Scaffoldの引数、floatingActionButton
```
FloatingActionButton(
    onPressed: 関数,
    tooltip: 'つーるちっぷ',
    child: Icon(Icons.star),
),
```
# Center
中央寄せ
```
Center(child: 内容)
```
# Column
縦並び
```
Column(
    mainAxisAlignment: MainAxisAlignment.centerとか,
    children <Widget>[内容]
)
```