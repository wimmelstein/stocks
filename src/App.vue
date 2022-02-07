<template>
  <StockList />
</template>

<script>
import StockList from './components/StockList.vue'
export default {
  name: 'App',
  components: {
    StockList,
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
}
body {
  margin: 100px;
  background-color: aliceblue;
}
td, th {
  text-align: left;
}
</style>
