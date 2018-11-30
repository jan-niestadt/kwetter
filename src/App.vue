<template>
  <div id="app">
    <img alt="INT kwetter logo" src="./assets/kwetter.png">
    <h1>Welkom bij INT Kwetter</h1>
    <MessageInput :initialMessage="placeholderText" :maxLength="60" />
  </div>
</template>

<script>
import MessageInput from './components/MessageInput.vue'

export default {
  components: {
    MessageInput
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
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;

}

#app img {
  width: 128px;
}
</style>