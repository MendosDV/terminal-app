<template>
  <div class="terminal text-white rounded-2">
    <div class="terminal-header rounded-top">
      <div class="terminal-buttons d-flex align-items-center h-100">
        <span class="rounded-circle"></span>
        <span class="rounded-circle"></span>
        <span class="rounded-circle"></span>
      </div>
    </div>
    <div class="terminal-window">

    </div>
  </div>
</template>

<script>
export default {
  name: 'TerminalApp',
}
</script>

<style lang="scss" scoped>
  .terminal {
    height: 55%;
    background-color: #040405;
    opacity: 0.9;;

    .terminal-header {
      background-color: #575151;
      width: 100%;
      height: 8%;

      .terminal-buttons {
        span {
          width: 14px;
          background-color: white;
          height: 14px;
        }
      }
    }

    @media screen and (max-width: 768px) {
      width: 100%;
    }

    @media screen and (min-width: 1024px) {
      width: 80%;
    }
  }
</style>
