
<template>
  <div>
    <main-game-component></main-game-component>
  </div>
</template>
<script>
import mainGameComponent from './components/main-game-component.vue'
export default {
  name: 'app',
  components: { mainGameComponent },
  data() {
    return {
      isDarkMode: true
    }
  }
}
</script>
<style scoped>
</style>
