# Color
ARGBの順
```
Color(0xFFFFFFFF)
```
```
Color.FromARGB(255,255,255,255)
```
# FlutterStudio
バージョンが古い  
バグ回避
```
{Key key}
```
↓
```
{Key? key}
```
テーマがうまく設定されない  
accentColorのプロパティがなくなってるなど
# テンプレート
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
上下左右中央寄せ
```
Center(child: 内容)
```
# Column / Row
縦並び
```
Column(
    mainAxisAlignment: MainAxisAlignment.startかMainAxisAlignment.centerかMainAxisAlignment.end, // Columnなら上下、Rowなら左右(並べる方向)
    crossAxisAlignment: ..., // MainAxisと交差する方向 , baselineとstretchもある
    mainAsixSize: MainAxisSize.minかMainAxisSize.max, // ウィジェットサイズ
    children <Widget>[内容]
)
```
# 
# Container
```
Container(
    child: 内容
)
```
# padding
例
```
padding: const EdgeInsets.all(10.0)
```
パディングを付けるためのウィジェット
```
Padding(
    padding: EdgeInsets.all(10.0),
    child: ...
)
```
# カスケード記法
式の値が同じままメソッド、プロパティを操作
```
Instance..Method()
```
式の値が同じ->同じオブジェクトに連続して使用できる
```
Instance..Method1()..Field1 = Data..Method2();
```
配列などでも
```
var a = <int>[1, 2, 3];
print(a..shuffle());
```
# TextButton
```
TextButton(
    onPressed: buttonPressed,
    child: Padding(
        padding: EdgeInsets.all(10.0),
        child: Text(
            "Push me!",
            style: TextStyle(),
        )
    )
)
```
テキスト以外でもいい
```
child:Icon (
    Icons.android,
    size: 50.0,
)
```
# ElevatedButton
Elevated->浮いた
```
ElevatedButton(
  onPressed:buttonPressed,
  child: Padding(
    padding: EdgeInsets.all(10.0),
    child:Icon (
      Icons.android,
      size: 50.0,
    )
  )
)
```
# IconButton
```
IconButton(
  icon: const Icon(Icons.insert_emoticon),
  iconSize: 100.0,
  color: Colors.red,
  onPressed:buttonPressed,
)
```
# FloatingActionButton
ScaffoldのfloatingActionButtonに渡すことが多い
```
FloatingActionButton(
  child: Icon(Icons.android),
  onPressed: buttonPressed
),
```
# RawMaterialButton
```
RawMaterialButton(
  fillColor: Colors.white,
  elevation: 10.0,
  padding: EdgeInsets.all(10.0),
  child: Text(
      "Push me!",
      style: TextStyle(fontSize:32.0,
      color: const Color(0xff000000),
      fontWeight: FontWeight.w400,
      fontFamily: "Roboto"),
    ),
  onPressed: buttonPressed
),
```
# TextField
```
TextField(
    onChanged: (String val){
        ...
    },
    controller: _controller,
    style: TextStyle(
        fontSize: 28.0,
        color: const Color(0xffFF0000),
        fontWeight: FontWeight.w400,
        fontFamily: "Roboto"),
)
```
# Checkbox
onChangedでvalueを変えないとステートが変更されない(setState)、自動で値が変更されたりはしない  
onChangedの引数はbool?
```
static var _checked = false;
...
Checkbox(
    value:_checked,
    onChanged: (bool? value){
        ...
    },
),
```
# Radio
groupValueの値をonChangedで変える
```
Radio<String>(
    value: 'A',
    groupValue: _selected,
    onChanged: (String? value){
        setState(() {
            _selected = value!;
        });
    },
)
```