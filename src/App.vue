<template>
  <div id="app">
    <div>
      <h1><img alt="INT kwetter logo" src="./assets/kwetter.png">Welkom bij INT Kwetter</h1>
      <MessageInput :initialMessage="placeholderText" :maxLength="40" />
    </div>
    <MessageList />
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
      placeholderText: "Typ hier iets."
    };
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