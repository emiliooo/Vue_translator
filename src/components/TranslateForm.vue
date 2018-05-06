<template>
  <div id="translateForm" class="row">
    <form class=" form-inline col-md-6 offset-md-5" v-on:submit="formSubmit">
      <input  class=" form-control" type="text" v-model="textToTranslate" placeholder="enter English word">
      <select class=" form-control" v-model="language">
        <option value="ru"> Russian </option>
        <option value="es"> Spanish </option>
        <option value="fr"> French </option>
        <option value="zh"> Chinese </option>
        <option value="pl"> Polish </option>
      </select>
      <input class="btn btn-primary"  type="submit" value="Translate">
    </form>
  </div>
</template>

<script>
  export default {
    name: 'translateForm',
    data(){
      return {
        textToTranslate:'',
        language:''
      }
    },
    created() {
      this.language = 'ru'

    },
    methods:{
      formSubmit(e){
        this.$emit('formSubmit', this.textToTranslate ,this.language );


        console.log(this.language )
        this.textToTranslate = ' '
        e.preventDefault();
      }

    }
  }
</script>

<style>



</style>
