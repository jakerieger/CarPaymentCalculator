<template>
  <div id="app">
    <h1>Car Payment Calculator</h1>
    <Calculator/>
  </div>
</template>

<script>
import '@/assets/style.css';
import Calculator from '@/components/Calculator.vue'

export default {
  name: 'App',
  components: {
    Calculator
  },
  beforeCreate() {
    document.title = 'Car Payment Calculator';
  }
}
</script>

<style>

</style>
