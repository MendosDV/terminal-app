<template>
  <div v-show="showTerminal" class="terminal text-white rounded-2">
    <div class="terminal-header rounded-top">
      <div class="terminal-buttons d-flex align-items-center h-100 px-2 gap-2">
        <span v-for="button in buttons" :key="button" :id="button" role="button" class="rounded-circle pointer" @click="button === 'red' ? toggleTerminal() : ''"></span>
      </div>
    </div>
    <div class="terminal-window">
    </div>
  </div>
</template>

<script>
export default {
  name: 'TerminalApp',
  data () {
    return {
      showTerminal: true,
      buttons: [ 'red', 'yellow', 'green'],
    }
  },
  methods: {
    toggleTerminal () {
      this.showTerminal = !this.showTerminal
    }
  },
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
        #red {
          background-color: #FF3B48;
        }

        #yellow {
          background-color: #FFC100;
        }

        #green {
          background-color: #00D742;
        }
      }
    }

    @media screen and (max-width: 768px) {
      width: 100%;

      span {
        width: 10px;
        height: 10px;
      }
    }

    @media screen and (min-width: 1024px) {
      width: 80%;

      span {
        width: 14px;
        height: 14px;
      }
    }
  }
</style>
