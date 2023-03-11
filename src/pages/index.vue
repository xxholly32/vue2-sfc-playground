<script setup lang="ts">
import { Repl, ReplStore } from 'vue2-repl'
import 'vue2-repl/dist/style.css'

const query = new URLSearchParams(location.search)
const store = new ReplStore({
  serializedState: location.hash.slice(1),
  showOutput: true,
  // showOutput: query.has('so'),
  outputMode: query.get('om') || 'preview',
  defaultvueEsmUrl: `https://unpkg.com/vue@2/dist/vue.esm.js`
})

watchEffect(() => history.replaceState({}, '', store.serialize()))

</script>

<template>
  <Repl @keydown.ctrl.s.prevent @keydown.meta.s.prevent :store="store" :showCompileOutput="true" :autoResize="true"
    :clearConsole="false" />
</template>
