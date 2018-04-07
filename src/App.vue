<template>
  <div class="text-center" id="app">
    <h1 >Simple Translator App</h1>
    <h5>Powerd by Vue.js</h5>
    <TranslateForm v-on:formSubmit="translateText"></TranslateForm>
    <TranslateOutput v-text="translatedText"></TranslateOutput>
  </div>
</template>

<script>

import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'App',
  components: {
    TranslateForm,
    TranslateOutput
  },
  data: function(){
    return{
      translatedText: ''
    }
  },

  methods: {
  translateText:function(text,language){
    this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180407T035437Z.96f276586c47b567.73b6af3550605be36e1275c4a56550c95c78228e&lang='+language+'&text='+text)
    .then((response)=>{
      this.translatedText = response.body.text[0];
    });
  }
  }
}
</script>

<style>
#app {

      padding-top: 1%
}
</style>
