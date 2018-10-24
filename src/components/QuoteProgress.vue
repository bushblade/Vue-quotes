<template>
  <div class="columns">
    <div class="column is-6 is-offset-3">
    <br>
      <h1 class="title has-text-centered">Quotes Added</h1>
      <h2 class="subtitle has-text-centered">{{ length }}/10</h2>
      <progress class="progress is-info is-medium" :value="length" max="10"></progress>
    </div>
  </div>  
</template>

<script>
export default {
  name: 'QuoteProgress',
  props: {
    length: Number
  }
}
</script>
<style>
  progress {
    -webkit-appearance: none;
  }
  .progress::-webkit-progress-value {
    transition : width 0.3s ease;
  }
</style>


