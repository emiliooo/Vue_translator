<template>
  <div class="text-center" id="app">
    <h1 >Word translator in VUE </h1>
    <h7 > by emil</h7>
    <TranslateForm v-on:formSubmit="translateText"> </TranslateForm>
    <TranslateOutput v-text="translatedText"> </TranslateOutput>
  </div>
</template>

<script>
  import TranslateForm from './components/TranslateForm'
  import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'App',
  components:{
    TranslateForm,
    TranslateOutput
  },
  data: function() {
    return {
      translatedText:''
    }
  },
  methods: {
    translateText:function (text,language) {

      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/' +
        'translate?key=trnsl.1.1.20180428T194509Z.77cbcc2ed3aa4c3d.194f3559fc50f4d92568bf66c19628b9703a3a11' +
        '&lang='+language+'&text=' + text).then(response => {

        // get body data


        this.translatedText =  response.body.text[0]

      }, response => {
        // error callback
      });


    }
  }
}
</script>

<style>

</style>
