<template>
  <div class="container">
    <appNewQuote @quoteAdded="newQuote"></appNewQuote>
    <appQuoteGrid :quotes="quotes" @quoteDeleted="deleteIt"></appQuoteGrid>
    <appHeader :quoteCount="quotes.length" :maxQuotes="maxQuotes" v-if="quotes.length > 0"></appHeader>
      <div class="row">
            <div class="col-sm-12 text-center">
                <div class="alert alert-info">Info: Click on a Quote to delete it!</div>
            </div>
        </div>
  </div>
</template>

<script>
import QuoteGrid from './components/QuoteGrid'
import NewQuote from './components/NewQuote'
import Header from './components/Header'

export default {
  data: function(){
    return {
      quotes: ['Destiny is not a matter of chance , it is a matter of choice'],
      maxQuotes: 10
    }
  },
  methods:{
    newQuote(quote){
      if(this.quotes.length >= this.maxQuotes){
       return alert('DELETE FIRST!');
      }
      this.quotes.push(quote);
    },
    deleteIt(index){
      this.quotes.splice(index, 1)
    }


  },
  components: {
    appQuoteGrid: QuoteGrid,
    appNewQuote: NewQuote,
    appHeader: Header
  }

}

</script>

<style>
</style>
