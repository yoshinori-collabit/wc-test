# webcomponents-sample

## Build
```bash
# 単品
npx vue-cli-service build --target wc --name vue-task --inline-vue src/components/HelloWorld.vue

# 複数コンポーネント
npx vue-cli-service build --target wc --name cb-task --inline-vue 'src/**/*.vue'

```

`--inline-vue` を付けると Vue もパッケージングしてくれる

Vue 使ってるページに組み込む場合、バージョン相違で問題出そう

## Props down, Emit Up
### props
```html
<custom-element string="string" number="111" array="[]"></custom-element>
```

props 側で type 設定されている前提で
- string
- number
- boolean
は認識する
  
Array は String で渡ってきた

例のごとく、中でキャメルケースだとしてもケバブケースで渡す

バインドだからといって : は必要ない

### emit
```html
<custom-element id="custom-element"></custom-element>
```

```javascript
// this.$emit('hoge', 1234) とされる想定
document.querySelector('#custom-element').addEventListener('hoge', (event) => {
    console.log(event.detail)
})
```

ちょっとめんどい
