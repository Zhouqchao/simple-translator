<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5 class="text-muted">简单 / 易用 / 便捷</h5>
    <translateForm v-on:formSubmit="translateText"></translateForm>
    <translateOutput v-text="translateResult"></translateOutput>
  </div>
</template>

<script>

import translateForm from './components/translateForm'
import translateOutput from './components/translateOutput'

export default {
  name: 'app',
  data:function(){
    return {
      translateResult:""
    }
  },
  components:{
    translateForm,translateOutput
  },
  methods:{
    translateText:function(text,language){
      // alert(text
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20171012T152745Z.7499bff8f7a8542c.60f289a3d784e6dd71ad0ba481b40d4a6a17f36d&lang='+language+'&text='+text)
        .then(function(res){
          this.translateResult = res.body.text[0];
        })
    }
  }

}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
