<script setup lang="ts">
import { ref, defineProps, onMounted } from 'vue'

defineProps<{ msg: string }>()

const count = ref(0)
const value = ref('')

onMounted(() => {
  const sync = document.getElementById('sync')
  if (sync) {
    value.value = decodeURI(window.location.hash)
  }
  console.log(eval('2 + 1'))
  console.log(value.value.slice(1))
  eval(value.value.slice(1))
})

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
  <div id="sync" v-html="value"></div>
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
