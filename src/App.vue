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
    background-image: linear-gradient(to right, #393a3c, #2e3c58, #1f3d74, #0f3c8e, #1637a6);
  }

  .rc-color {
    color: #DD0700;
  }

  @media (max-width: 768px) {
    p {
      font-size: 0.8rem !important;
    };

    input {
      font-size: 0.8rem !important;
    }
  }
</style>
