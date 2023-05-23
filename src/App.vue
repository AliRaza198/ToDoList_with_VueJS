<template>
  <toDoApp/>
</template>

<script>
import toDoApp from './components/toDoApp.vue'

export default {
  name: 'App',
  components: {
    toDoApp
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
