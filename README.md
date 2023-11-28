# Vue3Learning-MarkDown编辑器

## 环境配置

### npm init vite-app
### npm i
### npm i marked
### npm i lodash-es

## 主要代码
` const input = ref('# hello') `
#### 定义了一个名为 ‘input’ 的响应式变量，初值为 '# hello'，这是一个以 markdown 格式的字符串。
` const output = computed(() => marked(input.value)) `
#### ‘output’ 是一个计算属性，它包含了从 markdown 语法解析出来的 HTML。每当 ‘input’ 变化时，‘output’ 会自动更新。
` const update = debounce((e) => { input.value = e.target.value }) `
####  ‘update’ 函数被去抖，也就是说它不会立即执行。相反，它会在最后一次被触发后的一段指定时间过去之后才被执行。这在如实时搜索结果这样的场景中是有用的，因为你不希望函数随着用户的输入而不断执行。这里，‘update’ 函数会把 ‘input’ 的值更新为事件 ‘e’ 的值。

