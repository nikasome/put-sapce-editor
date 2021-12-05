<template>
  <div class="editor-area">
    <h1>{{ msg }}</h1>
  </div>
</template>

<script>
export default {
  name: 'Editor',
  props: {
    msg: String
  }
}
</script>

<style scoped>
.editor-area {
  margin-top: 10px;
}
</style>
