<template>
  <div id="app">
    <vuedraggable></vuedraggable>
  </div>
</template>

<script>
import vuedraggable from './components/vuedraggable.vue'

export default {
  name: 'app',
  components: {
    vuedraggable
  }
}
</script>

<style>
  body{margin: 0;padding: 0;}
</style>
