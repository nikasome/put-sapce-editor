<template>
  <Editor msg="入力すると自動でスペースが入力されます。"/>
</template>

<script>
import Editor from './components/Editor.vue'

export default {
  name: 'App',
  components: {
    Editor
  }
}
</script>

<style>
#app {
  color: #748799;
}
</style>
