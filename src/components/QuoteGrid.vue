<template>
  <div class="row">
      <appQuote v-for="(quote,index) in quotes" :key="index" @click.native="deleteQuote(index)">{{quote}}</appQuote>
  </div>                                                     <!-- 给vue组件标签绑定事件时候，必须加上native ，否则会认为监听的是来自组件自定义的事件-->
</template>

<script>
import Quote from './Quote';
export default {
    props: ['quotes'],
    components: {
        appQuote: Quote
    },
    methods:{
        deleteQuote(index){
            this.$emit('quoteDeleted', index);
        }
    }

}
</script>

<style>


</style>