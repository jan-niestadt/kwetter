<template>
  <div id="app">
    <div class='topbar'>
      <h1>Kwetter</h1>
    </div>
    <div class='components'>
      <MessageInput v-on:post-message="postMessage($event)" :placeholderText="placeholderText" :maxLength="40" />
      <MessageList :messages="messages" />
    </div>
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
      placeholderText: "Wat is er aan de hand?",
      messages: [
        {
          user: 'Jan',
          message: 'Test 1',
          time: new Date()
        },
        {
          user: 'Marco',
          message: 'Test 2',
          time: new Date()
        },
        {
          user: 'Mathieu',
          message: 'Test 3',
          time: new Date()
        }
      ]
    };
  },
  methods: {
    postMessage: function(message) {
      this.messages.push(message);

      /*
      Vue.axios.get(api).then((response) => {
        console.log(response.data)
      })
      */
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

img {
  float: left;
  width: 56px;
  padding-right: 10px;
}

h1 {
  padding: 10px;
  margin: 0;
}

.components {
  clear: both;
  /*
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: flex-start;
  */
}

</style>