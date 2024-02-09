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
        <pre id="ascii" role="img" aria-label="ASCII Radio Canada" class="mb-2 text-success">
__        __   _                             ____           _ _          ____                      _
\ \      / /__| | ___ ___  _ __ ___   ___   |  _ \ __ _  __| (_) ___    / ___|__ _ _ __   __ _  __| | __ _
 \ \ /\ / / _ \ |/ __/ _ \| '_ ` _ \ / _ \  | |_) / _` |/ _` | |/ _ \  | |   / _` | '_ \ / _` |/ _` |/ _` |
  \ V  V /  __/ | (_| (_) | | | | | |  __/  |  _   (_| | (_| | | (_) | | |__| (_| | | | | (_| | (_| | (_| |
   \_/\_/ \___|_|\___\___/|_| |_| |_|\___|  |_| \_\__,_|\__,_|_|\___/   \____\__,_|_| |_|\__,_|\__,_|\__,_|
        </pre>
        <div>
          <p class="fw-bold">Merci de venir consulter ce projet. Pour connaître la liste des commandes, tapez <span class="text-success">man</span>. Après chaque commande, vous pouvez la valider en appuyant sur <span class="text-success fst-italic">Enter</span>. Vous pouvez aussi appuyer sur <span class="text-success fst-italic">Tab</span> pour completer une commande.</p>
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
  }
};
</script>

<style lang="scss" scoped>
.terminal {
  height: 68%;
  background-color: #040405;
  opacity: 0.9;

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

    pre {
      display: block;
      font-family: monospace;
      white-space: pre;
    }
  }

  @media screen and (max-width: 480px) {
    width: 100%;

    span {
      width: 10px;
      height: 10px;
    }

    pre {
      font-size: 4px;
      text-align: left;
    }
  }

  @media screen and (min-width: 768px) {
    width: 100%;

    span {
      width: 10px;
      height: 10px;
    }

    pre {
      font-size: 10px;
    }
  }

  @media screen and (min-width: 1024px) {
    width: 80%;

    span {
      width: 14px;
      height: 14px;
    }

    pre {
      font-size: 10px;
    }
  }
}
</style>
