<template>
  <Indecision />
</template>

<script>
import Indecision from './components/Questions.vue'

export default {
  name: 'App',
  components: {
    Indecision
  }

}
</script>

<style

>
#app {
  font-family: Avenir, Arial, Helvetica, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2C3E50;
  margin-top: 60px;
}
</style>