<template>
  <div class="editor-area">
    <textarea class="put-space-editor" rows="3" cols="72" placeholder="文字を入力すると自動でスペースが入ります。" autofocus v-model="inputText"/>
    <textarea class="put-space-result" rows="3" cols="72" disabled v-model="putSpaceInputText"/>
  </div>
</template>

<script>
export default {
  name: 'Editor',
  data() {
    return {
      inputText: ''
    }
  },
  computed: {
    putSpaceInputText() {
      return this.inputText.split(/\n/).map(inputLine =>
        [...inputLine].join('　')
      ).join('\n')
    }
  }
}
</script>

<style>
.editor-area {
  margin-top: 10px;
  width: 540px;
}

.put-space-editor {
  resize: vertical;
  min-height: 30px;
  max-height: 360px;
  font-size: 14px;
}

.put-space-result {
  resize: vertical;
  min-height: 30px;
  max-height: 540px;
  font-size: 14px;
}
</style>
