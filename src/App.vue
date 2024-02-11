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
  body {
    overflow: hidden;
    background: linear-gradient(to right, #211f20, #292d34, #213030);
  }

  $rc-color: #5EC2B7;

  .rc-color {
    color: $rc-color;
  }

  #app {
    height: 100vh;
    width: 100vw;
    font-family: Ubuntu Mono,monospace;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    background: linear-gradient(to right, #211f20, #292d34, #213030);
  }

  ::-webkit-scrollbar {
      height: 4px;
      width:  8px;
    }

  ::-webkit-scrollbar-track {
    background: transparent;
  }

  ::-webkit-scrollbar-thumb {
    background: #5EC2B7;
    border-radius: 10px;
  }

  @media (max-width: 768px) {
    p, li, input, span, pre, div {
      font-size: 0.8rem !important;
    };
  }
</style>
