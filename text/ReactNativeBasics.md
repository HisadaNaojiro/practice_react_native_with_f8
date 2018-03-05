## React Nativeの基本構造

```
import React, { Component } from 'react'; // 1
import {
  Platform,
  StyleSheet,
  Text,
  View
} from 'react-native';

const instructions = Platform.select({ ... }); // 2

export default class App extends Component<{}> { ... } // 3

const styles = StyleSheet.create({ ... }); // 4

```

1. 必要なモジュールをインポート
2. プラットフォーム(ios,android)固有のメッセージを表示
3. UIを表すコンポーネント
4. コンポーネントのレイアウトと外観を制御するstyle

React NativeはES6Scriptを使用するため、通常のブラウザでは、使用することができない。
そこで、Babelというものを使用して、コンパイルする必要がある。

ES6Scriptには、Javascriptをより扱い易いようにするための構文が用意されている(class , アロー関数 etc...)

Reactのコンポーネントを作成する際は、
クラスで作るStatefullコンポーネント。
関数で作るStatelessコンポーネントがある。

クラスを作成する際は以下のようにReact Componentを継承させる
```
export default class App extends Component<{}> { ... } 
//export defaultで他のファイルでも使用できるようにする。
```

index.jsファイルを開くとAppRegistryというものがある
```
import { AppRegistry } from 'react-native';
import App from './App';

AppRegistry.registerComponent('PropertyFinder', () => App);
```
AppRegistryはReact Nativeアプリを動かすためのもの。
registerComponentでアプリを登録することによって、実際にアプリケーションが実行される


再びApp.jsに戻って、頭に以下を記述
```
'use strict';
```
これを記述することによってStrict Modeになる。
Strict Modeとはより厳格にjavascriptを扱うためのもので、曖昧な実装がエラー扱いになる。

App class内のrender()内を以下に変更
```
render() {
  return React.createElement(Text, {style: styles.description}, "Search for houses to buy!");
}

```

const styleを以下に変更
```
const styles = StyleSheet.create({
  description: {
    fontSize: 18,
    textAlign: 'center',
    color: '#656565',
    marginTop: 65
  },
});
```
ReactのJSXでは、styleをオブジェクト型で定義して、プロパティとして与えることができる。

記述できたら、エミュレータを更新させる。
表示が変更されていたら成功です。

React Nativeでは、android viewクラスは使いません。
代わりに、それと同等で軽量なUIを提供しています。
そして、
Reactコンポーネントのツリーを必要なネイティブUIに変換する処理を行います。

Android Studio内で、Tools\Android\Layout Inspectorを選択して、
次に、Show All Procesesにチェックを入れて、com.propertyfinderを選択し、OKをタップしてビュー階層を検査します。

すると、
WebViewインスタンスはなく、代わりにReactTextViewというものが呼ばれています。
ReactTextViewはTextViewを継承したものです。

android/app/src/main/java/com/propertyfinderに以下2つを開いてください。
- MainActivity.java
- MainApplication.java


