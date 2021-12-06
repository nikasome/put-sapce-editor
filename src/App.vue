<template>
  <div class="common-layout">
    <el-container>
      <el-header>文字の間にスペースを入力してくれるジェネレーター</el-header>
      <el-main><Editor/></el-main>
    </el-container>
  </div>
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
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
.el-header {
  text-align: center;
  line-height: 60px;
}
</style>
