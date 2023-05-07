# vue3leaflet-sample

## Vue3 + vue-leaflet で地図表示のサンプルコードです

コードの説明はQitta:[Vue3 + vue-leaflet で地図表示](https://qiita.com/items/65aaeb2bebabe00d62cd/)にあります。

動作は以下で確認できます：
- 　https://kyokonishito.github.io/vue3leaflet-sample/


`git clone`の後、以下のコマンドで動作します。
```
npm install
npm run dev
```

Build pathはgithub pages用に[vite.comfig.js](vite.config.js)を変更しています。
以下の設定をしています。
```
base: '/vue3leaflet-sample/',
  build: {
    outDir: 'docs'
  }
```