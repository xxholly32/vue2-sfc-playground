<script setup lang="ts">
import { isDark, toggleDark } from '~/composables'

const href = window.location.href
const copyLink = function () {
  var textArea = document.createElement("textarea");
    textArea.style.background = 'transparent';
    textArea.value = href;
    document.body.appendChild(textArea);
    textArea.select();
    document.execCommand("copy")
    document.body.removeChild(textArea);
    alert("url 复制成功！！！")
}
</script>

<template>
  <nav sm:flex tiny:hidden text-xl m-3 gap-2 justify-between>
    <div class="font-bold"><span>Vue2 SFC Playground</span></div>
    <div class="flex gap-2 items-center">
      <button class="icon-btn !outline-none" @click="toggleDark()">
        <div v-if="isDark" i-carbon-moon />
        <div v-else i-carbon-sun />
      </button>
      <button class="icon-btn !outline-none" title="复制链接" @click="copyLink()">
        <div i-carbon-copy-link />
      </button>
      <a class="icon-btn" i-carbon-logo-github rel="noreferrer"
        href="" target="_blank" title="Gitlab" />
      <a class="icon-btn" i-carbon-home rel="noreferrer" :href="href" target="_blank" title="去编辑" />
    </div>
  </nav>
  <div text-xl absolute class="left-2/4" z-10 top-2 sm:hidden tiny:block>
    <a class="icon-btn" i-carbon-home rel="noreferrer" :href="href" target="_blank" title="去编辑" />
  </div>
</template>