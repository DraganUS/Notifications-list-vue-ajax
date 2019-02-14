<template>
  <div id="app">
    <notification/>
  </div>
</template>

<script>
import notification from './components/notification.vue'

export default {
  name: 'app',
  components: {
    notification
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
  
}
</style>
