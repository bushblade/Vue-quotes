<template>
  <div class="container">
    <QuoteProgress :length="quotes.length"/>
    <QuoteInput :addquote="addQuote"/>
    <QuoteQuotes :parent="{ quotes, deleteQuote }"/>
    <QuoteFooter />
  </div>
</template>

<script>
import QuoteProgress from './components/QuoteProgress'
import QuoteInput from './components/QuoteInput'
import QuoteQuotes from './components/QuoteQuotes'
import QuoteFooter from './components/QuoteFooter'

export default {
  name: 'App',
  data() {
    return {
      quotes: [
        {
          text:
            'Realize deeply that the present moment is all you ever have. Make the Now the primary focus of your life.',
          author: 'Ekharte Tolle',
          id: Symbol('Ekharte Tolle')
        },
        {
          text:
            'I fear not the man who has practiced 10,000 kicks once, but I fear the man who has practiced one kick 10,000 times.',
          author: 'Bruce Lee',
          id: Symbol('Bruce Lee')
        },
        {
          text:
            'I have to completely rethink the problem in a certain way, but I think that’s just how software development goes because you would never get anything right just from the first try.',
          author: 'Evan You',
          id: Symbol()
        },
        {
          text: `There's something out there waiting for us, and it ain't no man. We're all gonna die.`,
          author: 'Billy - The Predator',
          id: Symbol('Billy - The Predator')
        },
        { text: `You see, I really love quotes.`, author: 'Maximilian Schwarzmüller', id: Symbol() }
      ]
    }
  },
  components: {
    QuoteProgress,
    QuoteInput,
    QuoteQuotes,
    QuoteFooter
  },
  methods: {
    addQuote(quote) {
      if (this.quotes.length < 10) {
        this.quotes.unshift(quote)
      }
    },
    deleteQuote(indx) {
      this.quotes.splice(indx, 1)
    }
  }
}
</script>

<style>
</style>