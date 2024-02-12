<template>
  <div v-show="showTerminal" class="terminal text-white rounded-2">
    <div class="terminal-header rounded-top">
      <div class="terminal-buttons d-flex align-items-center h-100 px-2 gap-2">
        <span v-for="button in buttons" :key="button" :id="button" role="button" class="rounded-circle pointer" @click="button === 'red' ? toggleTerminal() : ''">
        </span>
      </div>
    </div>
    <div class="terminal-body px-2 px-md-4">
      <div class="text-presentation">
        <pre id="ascii" role="img" aria-label="ASCII" class="mb-4 mb-md-2 ascii-text">
__        __   _                                                      _ _                  _
\ \      / /__| | ___ ___  _ __ ___   ___    _ __ ___  ___ _ __ _   _(_) |_ ___ _ __ ___  | |
 \ \ /\ / / _ \ |/ __/ _ \| '_ ` _ \ / _ \  | '__/ _ \/ __| '__| | | | | __/ _ \ '__/ __| | |
  \ V  V /  __/ | (_| (_) | | | | | |  __/  | | |  __/ (__| |  | |_| | | ||  __/ |  \__ \ |_|
   \_/\_/ \___|_|\___\___/|_| |_| |_|\___|  |_|  \___|\___|_|   \__,_|_|\__\___|_|  |___/ (_)
        </pre>
        <div>
          <p class="fw-bold">Thank you for checking out this project. To get the list of commands, type <span class="rc-color">man</span>. To execute a command, type <span class="rc-color fst-italic">Enter</span>. You can also press <span class="rc-color fst-italic">Tab</span> to autocomplete a command.</p>
        </div>
      </div>
      <TerminalWindow />
    </div>
  </div>
</template>

<script>
import TerminalWindow from './TerminalWindow.vue';

export default {
  name: 'TerminalApp',
  components: { TerminalWindow },
  data() {
    return {
      showTerminal: true,
      buttons: ['red', 'yellow', 'green'],
      showX: false,
    };
  },
  methods: {
    toggleTerminal() {
      this.showTerminal = !this.showTerminal;
    }
  },
};
</script>

<style lang="scss" scoped>
.terminal {
  height: 68%;
  background-color: #040405d4;
  opacity: 0.9;
  box-shadow: rgba(50, 50, 93, 0.25) 0px 50px 100px -20px, rgba(0, 0, 0, 0.3) 0px 30px 60px -30px;
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

  .terminal-body {
    height: 92%;
    overflow-y: scroll;

    ::-webkit-scrollbar {
      height: 4px;
    }

    ::-webkit-scrollbar-track {
      background: transparent;
    }

    ::-webkit-scrollbar-thumb {
      background: #5EC2B7;
      border-radius: 10px;
    }

    .ascii-text {
      font-size: 6px !important;
      text-align: left;

      @media screen and (min-width: 768px) {
        font-size: 10px !important;
      }

      @media screen and (min-width: 1024px) {
        font-size: 12px !important;
      }
    }
  }

  @media screen and (min-width: 0px) {
    width: 100%;

    span {
      width: 10px;
      height: 10px;
    }
  }

  @media screen and (min-width: 768px) {
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
