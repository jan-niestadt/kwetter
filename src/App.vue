<template>
  <div id="app">
    <h1>Kwetter</h1>
    <MessageInput v-model="newMessage" v-on:post-message="postMessage($event)" :maxLength="maxLength" />
    <MessageFeedback :value="newMessage" :maxLength="maxLength" />
    <MessageList :messages="messages" />
  </div>
</template>

<script>

import Vue from 'vue';
import MessageInput from './components/MessageInput.vue';
import MessageFeedback from './components/MessageFeedback.vue';
import MessageList from './components/MessageList.vue';

const BACKEND_URL = "https://gwtp.net/jn/kwetter.php";

export default {

  // Components die we gebruiken
  components: {
    MessageInput,
    MessageFeedback,
    MessageList
  },

  // Top-level app state
  data: function() {
    return {

      // Maximale lengte van een bericht
      maxLength: 40,

      // Berichten tot nu toe
      messages: [],

      // Het nieuwe bericht dat bewerkt wordt
      newMessage: {
        message: "",
        user: ""
      }
    };
  },

  // Wordt aangeroepen als de app voor het eerst start
  mounted: function () {
    // Get messages from backend
    Vue.axios.get(BACKEND_URL).then((response) => {
      this.messages = response.data;
    });
  },

  // Methods die je in bijv. event handlers kunt aanroepen
  methods: {

    // Post new message to backend
    postMessage: function() {
      let params = new URLSearchParams();
      params.append('message', this.newMessage.message );
      params.append('user', this.newMessage.user );
      params.append('time', (new Date()).getTime() );
      Vue.axios.post(BACKEND_URL, params).then((response) => {
        this.messages = response.data;
      });
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
  max-width: 15cm;
}

h1 {
  padding: 10px;
  margin: 0;
}

</style>