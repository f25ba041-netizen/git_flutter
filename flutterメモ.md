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
static final _controller = TextEditingController();
...
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
# DropdownButton
```
DropdownButton<型>(
    onChanged: (型? value){}
    value: 値,
    style: <<TextStyle>>,
    items: [<<DropdownMenuItem>>,...]
)
```
## DropdownMenuItem
```
DropdownMenuItem<型>(value: 値,child: ウィジェット)
```
# Align
位置揃え
```
Align(alignment:<<Alignment>>,child:...)
```
# PopupMenuButton
```
Align(
    alignment: Alignment.centerRight,
    child: PopupMenuButton(
        onSelected: (型 value){},
        itemBuilder: (BuildContext context) => <PopupMenuEntry<型>>[
            const PopupMenuItem(
                child: ウィジェット,
                value: 値
            ),
            ...
        ]
    )
)
```
# Slider
```
Slider(
    onChanged: (double value){},
    min: <<double>>,
    max: <<double>>,
    divisions: <<int>>, // 分割数、省略可(分割なし)
    value: <<double>>
)
```
# showDialog
```
showDialog(
    context: <<BuildContext>>,
    builder: <<WidgetBuilder>>
)
```
BuildContextはウィジェットのベース、State(自分自身)にcontextがあり、それを渡せばその画面上にダイアログが出る
## AlertDialog
```
showDialog(
    context: context,
    builder: (BuildContext context) => AlertDialog(
        title: ウィジェット,
        content: ウィジェット,
        actions: <Widget>[ウィジェットのリスト]
    )
)
```
actionsは下側に横並びで表示、通常はボタンなどを置く
## ダイアログから値の返却
ダイアログを閉じて値を返す処理
```
Navigator.pop<型>(<<BuildContext>>, 値)
```
呼び出し時に取得
```
showDialog(...).then<void>((型 value){})
```
# SimpleDialog
複数項目から1つを選ぶような入力
```
SimpleDialog(
    title: ウィジェット,
    children: [ウィジェットのリスト]
)
```
childrenには通常SimpleDialogOption
## SimpleDialogOption
```
SimpleDialogOption(
    child: ウィジェット,
    onPressed: (){}
)
```
# AppBar
```
AppBar(
    title: ウィジェット,
    leading: ウィジェット,
    actions: <Widget>[リスト],
    bottom: <<PreferredSize>>
)
```
画面構成  
leading | title | action action ...  
bottom  
## BackButton
戻るボタン、leadingによく置く
```
BackButton(
    color: <<Color>>
)
```
## PreferredSize
サイズを指定
```
PreferredSize(
    preferredSize: const Size.fromHeight(30.0),
    child: ウィジェット
)
```
# BottomNavigationBar
ScaffoldのbottomNavigationBarに配置  
画面の下部のナビゲーションバー  
アイコンなどを横並びに表示し、選択
```
BottomNavigationBar(
    currentIndex: <<int>>,
    items: <BottomNavigationBarItem>[リスト],
    onTap: (int value){} // インデックスが渡される
)
```
## BottomNavigationBarItem
```
BottomNavigationBarItem(
    label: <<String>>,
    icon: <<Icon>>
)
```
## Icon
```
Icon(
    <<Icons>>,
    color: <<Color>>,
    size: <<int>>
)
```
# ListView
```
ListView(
    shrinkWrap: <<bool>>, // 項目に応じて大きさを自動調整するか
    padding: <<EdgeInsets>>,
    children: <Widget>[リスト]
)
```
## ListTitle
ListViewのアイテムとして使用される
```
ListTitle(
    leading: <<Icon>>, // 左端に表示
    title: ウィジェット,
    selected: <<bool>>,
    onTap: (){}, // クリック
    onLongPress: (){} // 長押し
)
```
# SingleChildScrollView
スクロール表示
```
SingleChildScrollView(
    child: ウィジェット
)
```
# ナビゲーション
移動先をプッシュ
```
Navigator.push(<<BuildContext>>,<<Route>>)
```
移動をポップ
```
Navigator.pop(<<BuildContext>>)
```
## 画面切り替え
```
Navigator.push(
    context,
    MaterialPageRoute(builder: (context)=>ウィジェット)
)
```
PageRoute -> Routeのサブクラス  
MaterialPageRoute -> PageRouteのサブクラス  
PageRoute : 画面をPageRouteインスタンスに置き換え、元の画面をスタックに保管  
MaterialPageRouteで次の画面に表示するものを用意  
builderにはWidgetBuildという関数シグネチャ(特定の形式の関数のエイリアス)、`(context)=>ウィジェット`  
Navigatorのpopで戻る(スタックからPageRouteを取り出し、表示に戻す)
## 値の受け渡し
ウィジェットのコンストラクタに引数を追加  
遷移時に当てはめる
## routesでのルーティング
MaterialApp(最初に出すやつ)にルーティングを記述
```
MaterialApp(
    title: ...,
    theme: ...,
    initialRoute: "/",
    routes: {
        "/": (context) => ウィジェット,
        "/second": (context) => ウィジェット,
        ...
    }
)
```
画面遷移時に、routesに指定したキーを指定して遷移できる
```
Navigator.pushNamed(
    context,
    "指定したルーティングの文字列"
)
```