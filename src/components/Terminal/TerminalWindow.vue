<template>
  <div v-for="message in resultMessage" :key="message" class="result-message mb-2">
    <div v-if="Array.isArray(message[1])" class="result-message mb-2">
      <p class="text-secondary mb-2 d-flex align-items-center gap-3">
        Mickael ~$
        <span class="text-white">{{ message[0] }} </span>
      </p>
      <ul>
        <li v-for="command in message[1]" :key="command.name" class="fw-bold">
          <div v-if="command.name">
            <span class="rc-color">
              {{ command.name }}
            </span>
            : {{ command.description }}
          </div>
          <span v-else class="fst-italic ">
            {{ command.description }}
          </span>
        </li>
      </ul>
    </div>
    <div v-else class="result-message">
      <p class="text-secondary mb-2 d-flex align-items-center gap-3">
        Mickael ~$
        <span class="text-white">{{ message[0] }}</span>
      </p>
      <div>
        <div v-if="typeof message[1] === 'string' && isJSON(message[1])">
          <pre>{{ message[1] }}</pre>
        </div>
        <div v-else>
          {{ message[1] }}
        </div>
      </div>
    </div>
  </div>

  <div class="text-command d-flex align-items-center gap-3">
    <p class="text-secondary m-0">Mickael ~$</p>
    <input type="text" v-model="userInput" ref="commandInput" @keydown.enter.prevent="handleEnter" @keydown.tab.prevent="handleTab">
  </div>
</template>

<script>
export default {
  name: 'TerminalWindow',

  data() {
    return {
      userInput: '',
      resultMessage: [],
      manCommand: [
        { name: 'mickael', description: "Display the main information about Mickael"},
        { name: 'clear', description: '"Delete all displayed content' },
        { name: 'stack', description: "List Mickael's technical skills" },
        { name: 'cv', description: 'Download Mickael\'s CV' },
        { name: 'why', description: 'Display why you have to hire Mickael' },
        { name: 'coucou', description: 'afficher "Coucou c\'est moi"' },
        { description: 'Because time is money, you can use TAB key to autocomplete commands' },
        { description: 'To provide you with a better experience, you can find your previous orders using the arrows.' },
      ],
      mickaelCommand: '{"id":1,"name":"A green door","price":12.50,"tags":["home","green"]}',
      availableCommands: ['mickael', 'stack', 'cv', 'why', 'clear', 'coucou', 'man'],
    };
  },

  methods: {
    isJSON(str) {
      try {
        JSON.parse(str);
        true;
      } catch (e) {
        false;
      }
    },

    handleEnter() {
      const command = this.userInput.toLowerCase();
      const mickaelJson = JSON.stringify(JSON.parse(this.mickaelCommand), null, 2);
      console.log(typeof mickaelJson);

      switch (command) {
        case 'mickael':
          this.resultMessage.push(['mickael', mickaelJson]);
          break;
        case 'stack':
          this.resultMessage.push(['stack', "Coucou c'est moi"]);
          break;
        case 'cv':
          this.resultMessage.push(['cv', "Coucou c'est moi"]);
          break;
        case 'why':
          this.resultMessage.push(['why', "Coucou c'est moi"]);
          break;
        case 'clear':
          this.resultMessage = [];
          break;
        case 'coucou':
          this.resultMessage.push(['coucou', "Coucou c'est moi"]);
          break;
        case 'man':
          this.resultMessage.push(['man', this.manCommand]);
          break;
        default:
          this.resultMessage.push([this.userInput]);
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
