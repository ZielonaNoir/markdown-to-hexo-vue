<template>
  <div id="app">
    <h1>Markdown 图片链接转换器</h1>
    <textarea v-model="inputText" rows="10" placeholder="在此输入Markdown文本"></textarea>
    <button @click="convertMarkdownToHexo">转换</button>
    <textarea v-model="outputText" rows="10" placeholder="输出结果"></textarea>
  </div>
</template>

<script>
export default {
  data() {
    return {
      inputText: '',
      outputText: ''
    };
  },
  methods: {
    convertMarkdownToHexo() {
      const regex = /!\[(.*?)\]\((.*?)\)/g;
      this.outputText = this.inputText.replace(regex, (match, altText, url) => {
        return `{% img ${url} ${altText} %}`;
      });
    }
  }
};
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  margin: 20px;
  max-width: 600px;
}

textarea {
  width: 100%;
  margin: 10px;
  padding: 10px;
  font-size: 14px;
}

button {
  margin: 20px;
  padding: 20px 20px;
  font-size: 16px;
  cursor: pointer;
}
</style>
