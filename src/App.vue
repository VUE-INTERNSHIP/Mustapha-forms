<template>
  <div id="app">
    <formElements />
  </div>
</template>

<script>
import formElements from './components/formElements.vue'

export default {
  name: 'App',
  components: {
    formElements
  }
}
</script>

<style>
  *{
    margin:0;
    padding:0;
  }
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
}
</style>
