<template>
  <div id="app">
    <img class="img-fluid" src="./assets/cat.jpg" />
    <PromptPay />
  </div>
</template>

<script>
import PromptPay from './components/PromptPay.vue'

export default {
  name: 'App',
  components: {
    PromptPay,
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Kanit&display=swap');

#app {
  font-family: 'Kanit', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 5%;
}
</style>
