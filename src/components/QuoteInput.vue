<template>
  <div class="columns">
    <div class="column is-6 is-offset-3">
    <div class="field">
      <textarea class="textarea" placeholder="Enter a quote"
        v-model.trim="text"
        :class="textValid"
        ></textarea>    
    </div>
    <div class="field">
      <input class="input" type="text" placeholder="Author"
        v-model="author"
        :class="authorValid">    
    </div>
    <div class="field">
        <button class="button is-primary is-fullwidth is-outlined"
          @click="addNewQuote">Add Quote</button>    
    </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'QuoteInput',
  data(){
    return {
      text: null,
      textValid: '',
      author: null,
      authorValid: ''
    }
  },
  props: {
    addquote: Function
  },
  methods: {
    addNewQuote(){
      const { text, author, removeAnimations } = this
      let errorClasses = 'is-danger animated shake'
      if(text && author){
      this.addquote({text, author, id: Symbol(author)})
      this.text = null
      this.author = null
      } else if (text){
        this.authorValid = errorClasses
        removeAnimations()
      } else if (author){
        this.textValid = errorClasses
        removeAnimations()
      } else {
        this.authorValid = errorClasses
        this.textValid = errorClasses
        removeAnimations()
      }
    },
    removeAnimations(){
      setTimeout(() => {
        this.textValid = this.text ? 'is-success' : 'is-danger'
        this.authorValid = this.author ? 'is-success' : 'is-danger'
      }, 400)
    }
  },
  watch: {
    text(){
       this.textValid = this.text ? 'is-success' : ''
    },
    author(){
      this.authorValid = this.author ? 'is-success' : ''
    }
  }
}
</script>

