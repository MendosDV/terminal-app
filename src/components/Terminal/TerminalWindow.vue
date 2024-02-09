<template>
  <div>
    <div v-for="message in resultMessage" :key="message" class="result-message mb-2">
      <div v-if="Array.isArray(message)">
        <p class="text-secondary m-0">Mickael ~$</p>
        <p>Liste des commandes disponibles :</p>
        <ul>
          <li v-for="(item, index) in message" :key="index">{{ item }}</li>
        </ul>
      </div>
      <div v-else class="d-flex align-items-center gap-3">
        <p class="text-secondary m-0">Mickael ~$</p>
        {{ message }}
      </div>
    </div>
    <div class="text-command d-flex align-items-center gap-3">
      <p class="text-secondary m-0">Mickael ~$</p>
      <input type="text" v-model="userInput" ref="commandInput" @keydown.enter.prevent="handleEnter" @keydown.tab.prevent="handleTab">
    </div>
  </div>
</template>

<script>
export default {
  name: 'TerminalWindow',
  data() {
    return {
      userInput: '',
      resultMessage: [],
      availableCommands: ['clear', 'coucou', 'man'],
    };
  },
  methods: {
    handleEnter() {
      const command = this.userInput.toLowerCase();

      switch (command) {
        case 'clear':
          this.resultMessage = [];
          break;
        case 'coucou':
          this.resultMessage.push("Coucou c'est moi");
          break;
        case 'man':
          this.resultMessage.push([
            'clear : supprimer tout le contenu affiché',
            'coucou : afficher "Coucou c\'est moi"',
            'man : afficher la liste des commandes (clear, coucou, man)',
          ]);
          break;
        default:
          this.resultMessage.push(this.userInput);
          break;
      }

      this.userInput = '';
    },
    handleTab(event) {
      event.preventDefault();
      const userInputLowerCase = this.userInput.toLowerCase();
      const matchingCommands = this.availableCommands.filter(command => command.startsWith(userInputLowerCase));

      if (matchingCommands.length === 1) {
        this.userInput = matchingCommands[0];
      } else if (matchingCommands.length > 1) {
        this.resultMessage.push([ ...matchingCommands]);
      }
    },
  },
  mounted() {
    this.$refs.commandInput.focus();
  },
};
</script>

<style lang="scss" scoped>
  input {
    border: none;
    outline: none;
    background-color: transparent;
    color: #fff;
  }
</style>
