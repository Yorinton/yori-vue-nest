<script setup lang="ts">
import { ref, defineProps } from 'vue'

defineProps<{ msg: string }>()

const count = ref(0)
const value = ref('')
const onClick = () => {
  console.log(value.value)
  const sync = document.getElementById('sync')
  if (!sync) return
  document.head.innerHTML = value.value
  sync.innerHTML = value.value
}
</script>

<template>
  <p v-html="msg"></p>
  <a v-bind:href="value">
        click me
    </a>
  <button type="button" @click="count++">count is: {{ count }}</button>
  <p>
    Edit
    <code>components/HelloWorld.vue</code> to test hot module replacement.
  </p>
  <form @submit.prevent>
    <input type="text" v-model="value" @input="onInput" />
    <button @click="onClick">入力</button>
  </form>
  <div id="sync"></div>
</template>

<style scoped>
a {
  color: #42b983;
}

label {
  margin: 0 0.5em;
  font-weight: bold;
}

code {
  background-color: #eee;
  padding: 2px 4px;
  border-radius: 4px;
  color: #304455;
}
</style>
