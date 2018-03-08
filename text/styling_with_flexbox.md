## Flexboxによるスタイリング

これまでは、マージンやパディング、色などを扱う基本的なCSSを見てきました。

しかし、フレックスボックスは、様々な画面サイズで複雑なレイアウトを処理するのに便利な、CSS仕様に最近追加されたものです。

参考

https://qiita.com/takanorip/items/a51989312160530d89a1

React NativeはYogaというライブラリを使用してレイアウトをします。

YogaライブラリはFlexboxのC実装であり、Java(Android用)、Swift、Object-c、および、C#(.NET用)のバインディングを含んでいます。

通常は、YogaのflexDirection、alignItems、justifyContentの各プロパティを組み合わせてレイアウトを管理します。

現時点でのレイアウトには2つの子が垂直に配置されたコンテナがあります。

これは、アクティブな列のデフォルトのflexDirection値によるものです。

flexDirectionプロパティは、どの方向にアイテムを並べるか指定するもので、

主軸と交差軸を定義するのに役立ちます。

コンテナの主軸は垂直です。したがって、横軸は水平です。

alignItemsは、交差軸の子要素の配置を決定します。 

現時点では、この値を中央に設定しています。 

これは、子要素が中央に位置することを意味します。

SearchPage.jsを開き、2番目のTextエレメントの終了タグの直後に次のコードを挿入してください。
```
<View style={styles.flowRight}>
  <TextInput
    underlineColorAndroid={'transparent'}
    style={styles.searchInput}
    placeholder='Search via name or postcode'/>
  <Button
    onPress={() => {}}
    color='#48BBEC'
    title='Go'
  />
</View>
```

これで、テキスト入力とボタンを保持するビューを追加しました。

次に、コンテナスタイルの下に次の新しいスタイルを追加します。
```
flowRight: {
  flexDirection: 'row',
  alignItems: 'center',
  alignSelf: 'stretch',
},
searchInput: {
  height: 36,
  padding: 4,
  marginRight: 5,
  flexGrow: 1,
  fontSize: 18,
  borderWidth: 1,
  borderColor: '#48BBEC',
  borderRadius: 8,
  color: '#48BBEC',
},
```
これらは、テキスト入力とボタンの配置を設定します。

変更を保存し、再度、エミュレータで確認します。


テキストフィールドと移動ボタンは同じ行にあるため、

「flexDirection： 'row'」を使用するflowRightスタイルを使用してコンテナビューにラップして、横にアイテムを配置します。

また、テキスト入力に「flexGrow：1」を追加しました。 

Yogaは、最初に、サイズに応じてテキストの入力とボタンを配置します。 

次に、flexGrow値に従って残りの領域を分散します。 

したがって、テキスト入力は残りのスペースを引き継ぎます。
