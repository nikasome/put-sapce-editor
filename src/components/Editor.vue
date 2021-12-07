<template>
  <el-row>
    <el-col :span="12" :offset="6">
      <div class="label">入力</div>
      <el-input
        v-model="inputText"
        :autosize="{ minRows: 2 }"
        type="textarea"
        :placeholder="textAreaPlaceholder"
        autofocus
        maxlength="1000"
      />
      <div class="sub-label">{{ inputTextCount }}文字</div>
    </el-col>
  </el-row>
  <el-row>
    <el-col :span="12" :offset="6">
      <div class="label">出力</div>
      <el-input
        v-model="putSpaceInputText"
        :autosize="{ minRows: 2 }"
        type="textarea"
        :placeholder="putSpaceTextareaPlaceholder"
        disabled
      />
      <div class="sub-label">{{ putSpaceInputTextCount }}文字</div>
    </el-col>
  </el-row>
  <el-row>
    <el-col :span="12" :offset="6" style="text-align: end">
      <el-button type="text" @click="reset" style="margin-right: 12px;">削除</el-button>
      <el-button type="primary" @click="copy" :disabled="inputTextCount==0">コピー</el-button>
    </el-col>
  </el-row>
</template>

<script>
import { ElMessage } from "element-plus";
export default {
  name: "Editor",
  data() {
    return {
      inputText: "",
      textAreaPlaceholder: "文字を入力してください。",
      putSpaceTextareaPlaceholder: "文　字　を　入　力　し　て　く　だ　さ　い　。"
    }
  },
  methods: {
    reset() {
      this.inputText = "";
    },
    copy() {
      if (!this.putSpaceInputText.trim() == "")
      {
        navigator.clipboard.writeText(this.putSpaceInputText)
          .then(() => {
            ElMessage({
              showClose: true,
              message: "クリップボードにコピーしました。",
              type: "success",
              duration: 1000
            })
          })
          .catch(e => {
            console.error(e)
          });
      }
    }
  },
  computed: {
    inputTextCount() {
      return this.inputText.length
    },
    putSpaceInputText() {
      return this.inputText.split(/\n/).map(inputLine =>
        [...inputLine].join("　")
      ).join("\n")
    },
    putSpaceInputTextCount() {
      return this.putSpaceInputText.length
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
