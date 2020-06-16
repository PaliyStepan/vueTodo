<template>
  <div id="app">
    <Navbar />
    <Todos/>
  </div>
</template>

<script>
import Todos from './views/Todos';
import Navbar from  './components/Navbar'

export default {
  name: 'App',
  components: {
    Todos, Navbar
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
}
</style>
