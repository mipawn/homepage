<template>
  <div class="components-container">
    <!-- tui.editor -->
    <header>
      <div class="left-box">
        <div class="title">
          <input type="text" class="title-input" placeholder="请输入文章标题">
        </div>
      </div>
      <div class="right-box">
        <div class="status-text">文章将会自动保存至
          <a href="">草稿</a>
        </div>
        <div class="main-image-selector">图片</div>
        <div class="publish-popup">
          <div class="toggle-btn">
            <span class="titles">发布</span>
            <i class="icon ion-arrow-down-b">箭头</i>
          </div>
        </div>
      </div>
      <!-- <div class="submit">发布</div> -->
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
}
.title{
  display: flex;
  // -ms-flex-align: center;
  // align-items: center;
  // position: fixed;
  // top: 0;
  // left: 0;
  // right: 0;
  padding: 0 1.4rem;
  height: 5.334rem;
  background-color: #fff;
  border-bottom: 1px solid #ddd;
  // z-index: 100;
}
.title-input{
  margin: 0;
    padding: 0;
    font-size: 2rem;
    font-weight: 700;
    color: #000;
    border: none;
    outline: none;
    flex: 1 1 auto;
}
.right-box{
  // justify-content: flex-end;
  display: flex;
  align-items: center;
}
.status-text{
  font-size: 1.334rem;
  white-space: nowrap;
  color: #ddd;
  cursor: default;
}
.status-text a{
  margin: 0 0 0 .4em;
  padding: .2em .4em;
  color: inherit;
  text-decoration: none;
  border: 1px solid currentColor;
  border-radius: 2px;
}
.main-image-selector{
  padding-left: 1.2rem;
  padding-right: 1.2rem;
}
.publish-popup{
  display:flex;
  padding-left: 1.2rem;
  padding-right: 1.2rem;
}
.toggle-btn{
  font-size: 1.334rem;
    white-space: nowrap;
    color: #007fff;
    cursor: pointer;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
}

.submit {
  color: #1890ff;
}
</style>
