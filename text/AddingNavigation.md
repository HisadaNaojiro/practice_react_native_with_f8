React Navigationとは、パッケージの1つで、React Nativeアプリの使いやすいナビゲーションを提供してくれるものです。

Javascriptで実装されているため、IOSとAndroidの両方で動作します。

以下のコードをターミナル上で入力してパッケージをインストールしてください。

```
npm install --save react-navigation
```

インストールできましたら、React Navigationを使用する準備ができました。

React Navigationを使用するために、App.jsファイルのimport箇所に以下を記述してください

```
import {StackNavigator} from 'react-navigation';
```

StackNavigatorは、新しい画面がスタックの上に配置される画面間でアプリを移行する方法を提供してくれます。

次にAppクラスの定義を以下のように置き換えてください。
```
class SearchPage extends Component<{}> 
```

次に、SearchPageクラスのrender()の直前に以下を記述してください
```
static navigationOptions = {
  title: 'Property Finder',
};
```

これは、この画面のナビゲーションバーにタイトルを設定します。

最後にSearchPageコンポーネントの下に以下を記述してください。
```
const App = StackNavigator({
  Home: { screen: SearchPage },
});

const styles = ...

export default App;
```
エミュレーターを起動してナビゲーションが構築されているか確認してください。
