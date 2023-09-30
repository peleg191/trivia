
<template>
  <div class="app-body">
    <template v-if="menu == 0">
      <main-menu-component :level="level" :exp="exp" @start-game="menu = 1"></main-menu-component>
    </template>
    <template v-else>
      <main-game-component :level="level" :exp="exp"  @back-to-menu="menu = 0" ></main-game-component>
    </template>
  </div>
</template>
<script>
import mainGameComponent from './components/main-game-component.vue';
import mainMenuComponent from './components/main-menu-component.vue';
import storage from './storage';
export default {
  name: 'app',
  components: { mainGameComponent,mainMenuComponent },
  data() {
    return {
      isDarkMode: true,
      menu:0,
      level:1,
      exp:0
    }
  },
  watch:{
    menu:{
      immediate:true,
      handler(){
        this.getData();
      }
    }
  },
  methods:{
    getData(){
      this.level = storage.getItem('level') || 1 ;
      this.exp = storage.getItem('exp') || 0 ;
    }
  }
}
</script>
<style scoped>
.app-body{
    height: 100vh;
    width: 100vw;
    background: #282828;
    font-family:'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
}
</style>
