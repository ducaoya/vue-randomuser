<template>
  <RandomUser />
</template>

<script>
import RandomUser from './components/randomuser'
export default {
  name: 'App',
  components: {
    RandomUser
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


</style>
