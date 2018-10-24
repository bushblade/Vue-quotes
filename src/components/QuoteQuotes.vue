<template>
  <transition-group tag="div" class="columns is-multiline quotes"
    name="quote">
    <div class="column is-one-quarter-desktop is-one-third-tablet quote-item"
      v-for="(quote, indx) of parent.quotes"
      :key="quote.id">
      <article class="message"
          :class="hoverStyle(indx)"
          @mouseover="hoverIndex = indx"
          @mouseout="hoverIndex = null"        
          @click="parent.deleteQuote(indx)">
          <div class="quote message-body">
              <i class="fas fa-quote-left"></i> 
              {{ quote.text }} 
              <i class="fas fa-quote-right"></i>
              <em class="author">~{{ quote.author }}~</em>
          </div>
        </article>    
    </div>
  </transition-group>      
</template>

<script>
export default {
  data(){
    return {
      hoverIndex: null
    }
  },
  name: 'QuoteQuotes',
  props: {
    parent: Object
  },
  methods: {
    hoverStyle(indx){
      return this.hoverIndex === indx ? 'is-warning quote-shadow' : 'is-dark' 
    }
  }
}
</script>

<style>
 .quote-item {
   font-family: 'Merienda', cursive;
   cursor: pointer;
   transition: all 0.5s;
 }
 .author {
   display: block;
   margin: 0.5em;
 }

.quote-enter, .quote-leave-to {
  opacity: 0;
  transform: translateX(-100%);
}
.quote-leave-active {
  position: absolute;
}

.quote-shadow {
  box-shadow: 0px 0px 16px 2px rgba(0,0,0,0.1);
}
</style>
