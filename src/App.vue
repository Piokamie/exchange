<template>
  <div id="app">
<ExchangeView></ExchangeView>
  </div>
</template>

<script>
import ExchangeView from "@/components/ExchangeView.vue";
export default {
  name: 'App',
  components: {
    ExchangeView
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
