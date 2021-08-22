<template>
  <div class="app flex">
    <LeftSide/>
    <Main/>
  </div>
</template>

<script>
import LeftSide from './components/LeftSide.vue'
import Main from './components/Main.vue'

export default {
  name: 'App',
  components: {
    LeftSide,
    Main
  }
}
</script>

<style lang="scss">
@import './styles/general.scss';
@import './styles/utilities.scss';

  .app{
    height: 100vh;
  }
</style>
