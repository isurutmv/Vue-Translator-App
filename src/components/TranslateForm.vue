<template>
  <div class="container" id="translateForm">
    <form v-on:submit="formSubmit" id="formtranslate">
<fieldset>
  <div class="form-group row">
      <input type="text" v-model="word" placeholder="Enter Your Word........">
        <select v-model="language">

          <option value="si">Sinhala</option>
          <option value="ru">Russion</option>
          <option value="zh">Chinese</option>
          <option value="ja">Japanese</option>
          <option value="hi">Hindi</option>

        </select>

        <input class="btn btn-primary" type="submit" value="Translate">
  </div>
        </fieldset>
    </form>

  </div>
</template>

<script>
export default {
   name: 'translateForm',
   data(){
     return{
        word: null,
        language: null
     }
   },
   created(){
     this.language = 'si';
   },
   methods: {
     formSubmit(e){
       this.$emit('formSubmit',this.word,this.language);
       e.preventDefault();


     }
   }
}
</script>

<style>
   #formtranslate{

           padding-left: 35%
   }

</style>
