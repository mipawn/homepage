<template>
  <div class="components-container">
    <!-- tui.editor -->
    <header>
      <div class="title">
        <input type="text" placeholder="请输入文章标题">
      </div>
      <div class="submit">发布</div>
    </header>
    <section />
    <div class="editor-container">
      <markdown-editor ref="markdownEditor" v-model="content1" height="300px" :language="language" />
    </div>
    <el-button style="margin-top:80px;" type="primary" icon="el-icon-document" @click="getHtml">
      Get HTML
    </el-button>
    <div v-html="html" />
  </div>
</template>

<script>
import MarkdownEditor from '@/components/MarkdownEditor'

const content = `
**This is test**

* vue
* element
* webpack

`
export default {
  name: 'Markdown',
  components: { MarkdownEditor },
  data() {
    return {
      content1: content,
      content2: content,
      content3: content,
      content4: content,
      html: '',
      languageTypeList: {
        'en': 'en_US',
        'zh': 'zh_CN',
        'es': 'es_ES'
      }
    }
  },
  computed: {
    language() {
      return this.languageTypeList['zh']
    }
  },
  methods: {
    getHtml() {
      this.html = this.$refs.markdownEditor.getHtml()
      console.log(this.html)
    }
  }
}
</script>

<style scoped lang="scss">
.editor-container{
  margin-bottom: 30px;
}
header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 100px;
}
.submit {
  color: #1890ff;
}
</style>
