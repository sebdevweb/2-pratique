<script setup>

  import { computed, ref } from 'vue'
  import { marked } from 'marked'
  import { debounce } from 'lodash-es'

  const input = ref('# Hello!')
  const output = computed(() => marked(input.value))
  const update = debounce((e) => {
    input.value = e.target.value
  }, 100)
  

</script>

<template>
  <div class="editor">
    <textarea class="input" :value="input" @input="update"></textarea>
    <div class="output" v-html="output"></div>
  </div>
</template>

<style>
  .editor {
    height: 100vh;
    display: flex;
  }
  input, .output {
    overflow: auto;
    width: 50%;
    height: 100%;
    box-sizing: border-box;
    padding: 0 20px;
  }

  .input {
    border: none;
    border-right: 1px solid #ccc;
    resize: none;
    outline: none;
    background-color: #f6f6f6;
    font-size: 14px;
    font-family: 'Monaco', Couriern monospace;
    padding: 20px;
  }
  code  {
    color: #f66;
  }
</style>
