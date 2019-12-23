<template>
  <div id="app">
    <Home msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import Home from './components/Home.vue'

export default {
  name: 'app',
  components: {
    Home
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.m-div {
  display: inline-flex;
  margin: 5px;
}
table.m-table {
  display: inline-block;
}
.m-table, .m-table th, .m-table td {
    border-width: 1px;
    border-style: ridge;
    border-collapse: collapse;
    width: 280px;
	vertical-align: bottom;
}
.opaque {
  opacity: 1.0;
}
.transparent {
  opacity: 0.1;
}
</style>
