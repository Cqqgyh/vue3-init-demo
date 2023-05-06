<script setup>
import {reactive, ref, watch} from 'vue'

defineProps({
  msg: String,
})

const count = ref(0)
// todo start bug
const part2RightTextList = reactive([
	{
		text: 'demo',
		isChecked: true,
	},

])
watch( ()=> part2RightTextList, (newValue, oldValue) => {
	part2RightTextList[0].isChecked = !!newValue.every(item => !item.isChecked);
}, {immediate: true, deep: true})
// end bug
</script>

<template>
  <h1>{{ msg }}</h1>

  <div class="card">
    <button type="button" @click="count++">count is {{ count }}</button>
    <p>
      Edit
      <code>components/HelloWorld.vue</code> to test HMR
    </p>
  </div>

  <p>
    Check out
    <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank"
      >create-vue</a
    >, the official Vue + Vite starter
  </p>
  <p>
    Install
    <a href="https://github.com/vuejs/language-tools" target="_blank">Volar</a>
    in your IDE for a better DX
  </p>
  <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
