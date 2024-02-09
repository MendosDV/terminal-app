<template>
  <div class="container-md d-flex justify-content-center align-items-center h-100">
    <TerminalApp />
  </div>
</template>

<script>
import TerminalApp from './components/Terminal/TerminalView.vue'

export default {
  name: 'App',
  components: { TerminalApp },
}
</script>

<style lang="scss">
  #app {
    height: 100vh;
    width: 100vw;
    font-family: Ubuntu Mono,monospace;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    background: hsla(120, 6%, 90%, 1);
    background: linear-gradient(90deg, hsla(120, 6%, 90%, 1) 0%, hsla(228, 75%, 16%, 1) 100%);
    background: -moz-linear-gradient(90deg, hsla(120, 6%, 90%, 1) 0%, hsla(228, 75%, 16%, 1) 100%);
    background: -webkit-linear-gradient(90deg, hsla(120, 6%, 90%, 1) 0%, hsla(228, 75%, 16%, 1) 100%);
  }

  .rc-color {
    color: #DD0700;
  }

  @media (max-width: 768px) {
    p, li, input, span, pre, div {
      font-size: 0.8rem !important;
    };
  }
</style>
