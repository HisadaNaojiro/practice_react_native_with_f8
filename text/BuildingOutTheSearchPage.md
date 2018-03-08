SearchPage.jsという名前の新しいファイルを追加し、App.jsと同じフォルダに配置してください。

SearchPage.jsに以下コードを記述してください。
```
'use strict';

import React, { Component } from 'react';
import {
  StyleSheet,
  Text,
  TextInput,
  View,
  Button,
  ActivityIndicator,
  Image,
} from 'react-native';
```

これらのインポートしたモジュール群は、UI構築に必要なものです。

import構文の下にSearchPageクラスを作成していきます。
以下コードをimport構文の下に記述してください。
```
export default class SearchPage extends Component<{}> {
  static navigationOptions = {
    title: 'Property Finder',
  };

  render() {
    return (
      <View style={styles.container}>
        <Text style={styles.description}>
          Search for houses to buy!
        </Text>
        <Text style={styles.description}>
          Search by place-name or postcode.
        </Text>
      </View>
    );
  }
}
```

次に、SearchPageクラスの下にStyleを記述していきます。
以下コードをSearchPageクラスの下に記述してください。
```
const styles = StyleSheet.create({
  description: {
    marginBottom: 20,
    fontSize: 18,
    textAlign: 'center',
    color: '#656565'
  },
  container: {
    padding: 30,
    marginTop: 65,
    alignItems: 'center'
  },
});
```

SearchPageクラスを記述できましたら、App.jsにimportします。
```
import SearchPage from './SearchPage';
```
importできましたら、App.jsファイルに記述してあるSearchPageクラスとSearchPageクラスに関連するスタイル等を削除してください。

変更を保存して、再度エミュレータを開き、新しいUIを確認してください。
