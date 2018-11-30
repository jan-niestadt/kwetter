<template>
  <div id="app">
    <div>
      <h1><img alt="INT kwetter logo" src="./assets/kwetter.png">Welkom bij INT Kwetter</h1>
      <MessageInput v-on:post-message="postMessage($event)" :initialMessage="placeholderText" :maxLength="40" />
    </div>
    <MessageList :messages="messages" />
  </div>
</template>

<script>
import MessageInput from './components/MessageInput.vue'
import MessageList from './components/MessageList.vue'

export default {
  components: {
    MessageInput,
    MessageList
  },
  data: function() {
    return {
      placeholderText: "Typ hier iets.",
      messages: [
        'Is het "dat lemma" of "dilemma"? ;-)',
        'Gele kaart voor slechte woordgrappen!',
        'Zalmsalade op brood vandaag. Yum!'
      ]
    };
  },
  methods: {
    postMessage: function(message) {
      this.messages.push(message);
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}

img {
  width: 64px;
}

h1 {
  padding-top: 0;
}
</style>