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
        { name: 'clear', description: '"Delete all displayed content' },
        { name: 'mickael', description: "Display the main information about Mickael"},
        { name: 'stack', description: "List Mickael's technical skills" },
        { name: 'cv', description: 'Download Mickael\'s CV' },
        { name: 'why', description: 'Display why you have to hire Mickael' },
        { name: 'like', description: 'Will send me a like for this project automatically' },
      ],
      stackCommand: [
        { name: 'Backend', description: "Ruby on Rails, Node.js, actually learning C#." },
        { name: 'Frontend', description: 'HTML, CSS, React, Vue.js, Bootstrap, Tailwind.' },
        { name: 'Database', description: "MySQL, PostgreSQL, MongoDB." },
      ],
      mickaelCommand: '{"first_name":"Mickael","last_name":"Riss","age":25,"email":"mickaelriss6@gmail.com","website":"www.mickael-riss.com","job":"Software Developer","city":"Montréal"}',
      whyCommand: "Parce que je possède une solide expérience dans le développement logiciel, avec des compétences approfondies dans les technologies telles que JavaScript, React, et Node.js. En plus de mes compétences techniques, j'apporte une attitude positive et une passion pour résoudre des problèmes complexes. Ma capacité à collaborer efficacement au sein d'une équipe et à communiquer clairement fait de moi un membre précieux de tout projet.",
      availableCommands: ['mickael', 'stack', 'cv', 'why', 'clear', 'coucou', 'man', 'like'],
    };
  },

  methods: {
    handleDocumentClick(event) {
      if (!this.$refs.commandInput.contains(event.target)) {
        this.$refs.commandInput.focus();
      }
    },

    isJSON(str) {
      try {
        JSON.parse(str);
        return true;
      } catch (e) {
        return false;
      }
    },

    downloadCV() {
      const link = document.createElement('a');
      link.href = '/CV_Mickael_Riss.pdf';
      link.download = 'CV_Mickaël_Riss.pdf';
      link.click();
    },

    handleEnter() {
      const command = this.userInput.toLowerCase();
      const mickaelJson = JSON.stringify(JSON.parse(this.mickaelCommand), null, 2);

      switch (command) {
        case 'mickael':
          this.resultMessage.push(['mickael', mickaelJson]);
          break;
        case 'stack':
          this.resultMessage.push(['stack', this.stackCommand]);
          break;
        case 'cv':
          this.downloadCV();
          this.resultMessage.push(['cv', 'Downloading CV...']);
          break;
        case 'why':
          this.resultMessage.push(['why', this.whyCommand]);
          break;
        case 'clear':
          this.resultMessage = [];
          break;
        case 'man':
          this.resultMessage.push(['man', this.manCommand]);
          break;
        case 'like':
          this.resultMessage.push(['like', this.manCommand]);
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
    document.addEventListener('click', this.handleDocumentClick);
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
