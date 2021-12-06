<template>
  <el-row>
    <el-col :span="16" :offset="4">
      <div class="label">入力</div>
      <el-input
        v-model="inputText"
        :autosize="{ minRows: 2 }"
        type="textarea"
        placeholder="文字を入力すると自動でスペースが入ります。"
        autofocus
        maxlength="1000"
      />
      <div class="sub-label">文字数</div>
    </el-col>
  </el-row>
  <el-row>
    <el-col :span="16" :offset="4">
      <div class="label">出力</div>
      <el-input
        v-model="putSpaceInputText"
        :autosize="{ minRows: 2 }"
        type="textarea"
        placeholder="自動でスペースが入った文字がここに出ます。"
        disabled
      />
      <div class="sub-label">文字数</div>
    </el-col>
  </el-row>
  <el-row>
    <el-col :span="16" :offset="4" style="text-align: end">
      <el-button type="text" style="color: var(--el-color-danger); margin-right: 12px;">削除</el-button>
      <el-button type="primary">コピー</el-button>
    </el-col>
  </el-row>
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
.el-row {
  margin-bottom: 20px;
}
.label {
  font-size: var(--el-font-size-medium);
  color: var(--el-color-info);
}
.sub-label {
  font-size: var(--el-font-size-base);
  color: var(--el-color-info);
  text-align: end;
}
</style>
