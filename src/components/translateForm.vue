<template>
  <div class="row" id="translateForm">
    <div class="col-md-6 col-md-offset-3">      
      <form id="transForm" class="well form-inline" @submit="formSubmit">
        <input class="form-control" type="text" placeholder="请输入需要翻译的内容" v-model="textToTranslate">
        <select class="form-control" v-model="language">
          <option value="en">English</option>
          <option value="ru">Russia</option>
          <option value="ko">Korean</option>
        </select>
        <input class="btn btn-primary" type="submit" value="翻译">
      </form>
    </div>
  </div>
</template>

<script>


export default {
  name: 'translateForm',
  data:function(){
    return {
      textToTranslate:"",
      language:""
    }
  },
  methods:{
    formSubmit:function(e){
      e.preventDefault();
      // alert(this.textToTranslate);
      this.$emit("formSubmit",this.textToTranslate,this.language);
    }
  },
  created:function(){
    this.language = 'en';
  }

}
</script>

<style>
  #transForm{
    border:1px solid #ccc;
    border-radius: 10px;
  }
</style>
