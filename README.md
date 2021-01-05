# first_flutter_app

リストを作るにはListView Widgetを使い、子要素にListTileを行として使うイメージ
ちなみにListViewではなくColumn widgetとかにすると、スクロール対応しなくなって、画面からはみ出ている対応不可なものとして扱われる。
ListTile内にonTapを追加し、画面遷移のコードをいれることでルーティングしたページへ移動することができる
さらにその中で  MaterialPageRoute(builder: (context) => NextPage('次にきた')),  のように次の画面へデータを渡すことも可能

final items = List.generate(100, (i) => "Item $i");
は変数にリスト(List.generate)を代入してる
100は0から99までの100件、(i)はインデックスが入っている
ここでいうインデックスは添字のこと
itemCount: items.length, はitemsの個数(長さ)を指す

crossAxisCountは横何列のリストにするかを指定


画面から画面はデータを渡すにはonPressed内のコードで渡したい画面のルートに情報を書き、渡されたページで
  NextPage(this.name);
  final String name; と書く。nameは変数名

async, await で一旦処理を停止することができる。asyncからawaitまでの処理を実行し停止、次の処理を動かした時続きの処理が再開する

widgetを重ねてアプリのUIを作る

Column Widgetは縦に並ぶ
Row Widgetは横に並ぶ。>>ブロック要素とインライン要素みたいなもの？

option と enter でcenterとかcolumn、row widgetを簡単に入れられる

Container Widgetはただの箱
height: double.infinity は全体の高さにするってことかな？

RaisedButtonというボタンのWidget。他にもFlatButton、OutlineButtonなど様々なボタンがある
onPressedでボタンを押せるようになる。この中に画面遷移のコードなどを書く

新しいファイル(dart)を作ってクラス名を指定した時、赤い波アンダーバーをクリック、「Create 1 missing override」を押すと自動で雛形?みたいなのを作ってくれる
importにはcupertinoかmaterialが入っていればOK

onPressedの中に書く画面遷移のコードは公式からコピペするとかでOK
この中に Navigator.pop(context); を入れることで前のページに戻るボタンが作れる;

画面遷移にはルーティングを最初に決めてやる方法もある。が、エラーがどうしても解決できなかったので割愛

printでコンソールに出力できる

画像出力には、image.networkに画像のURLのを入れる
const Image(
  image: NetworkImage()
), で、image: NetworkImage()内にURLを入れても表示できる

PC上ディレクトリ内にある画像を表示する時
Widget内にImage.asset('images/sample_png.png')
と書くだけじゃエラーが出るので
pubspec.yaml の flutter下にパスを指定してあげる
assets:
    - images/sample.png みたいな感じ
    
フォームを作る時は child: TextField() でできる、（）を内にCSSみたいな感じで装飾可能
TextFromFieldでフォームを作ったらvalidationとかもできるから、実装するときはこっちのほうがいいかも
TextField 内に autofocus: true があると、その画面を開いた時に自動でキーボードが出てくるようになる。UI/UX的に良いかも

FocusNode処理の変数.requestFocus() をonPressed内に入れると、そのボタンを押すとフォームにフォーカスされるような処理にできる

COOKBOOK
final myController = TextEditingController();
は、別の場所で入力された情報を取得する場合に使い
onChanged: (text) {
  name = text;
}, は都度入力に応じて情報を取得する場合に使うために変数に入れる