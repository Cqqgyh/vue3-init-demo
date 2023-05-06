# /src/components/HelloWorld.vue
## bug
```js
// todo start bug
const part2RightTextList = reactive([
{
text: 'demo',
isChecked: true,
}
])
// 如果在目录中解开注释，打包后将无法预览查看
// 重现条件：同时使用{immediate: true, deep: true}
watch( ()=> part2RightTextList, (newValue, oldValue) => {
part2RightTextList[0].isChecked = !!newValue.every(item => !item.isChecked);
}, {immediate: true, deep: true})
// end bug
```

