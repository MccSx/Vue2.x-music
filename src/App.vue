<template>
  <div id="app">
    <m-header></m-header>
    <v-tab></v-tab>
    <keep-alive>
      <router-view></router-view>
    </keep-alive>
    <v-player></v-player>
  </div>
</template>

<script>
import MHeader from './components/m-header/m-header'
import Tab from './components/tab/tab'
import Player from './components/player/player'

export default {
  name: 'app',
  components: {
    'm-header': MHeader,
    'v-tab': Tab,
    'v-player': Player
  }
}
</script>

<style scoped lang="stylus" rel="stylesheet/stylus">
  
</style>
