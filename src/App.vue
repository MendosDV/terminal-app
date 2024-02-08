<template>
  <div class="container-md d-flex justify-content-center align-items-center h-100">
    <TerminalApp />
  </div>
</template>

<script>
import TerminalApp from './components/Terminal/TerminalView.vue'

export default {
  name: 'App',
  components: { TerminalApp }
}
</script>

<style lang="scss">
  #app {
    height: 100vh;
    width: 100vw;
    font-family: Ubuntu Mono,monospace;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    background: rgb(2,0,36);
    background: linear-gradient(90deg, rgba(2,0,36,1) 0%, rgba(26,26,105,1) 35%, rgba(0,212,255,1) 100%);
  }
</style>
