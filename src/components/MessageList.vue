<template>
  <div class='messageList'>
    <h2>Berichten</h2>
    <ul>
      <Message v-for="(message, index) in messages" :message="message" :index="index" :key="index" />
    </ul>
  </div>
</template>

<script>
import Message from './Message.vue'

export default {

  // Values this component receives from its parent
  // Don't change these inside the component!
  props: {
    messages: Array
  },

  components: {
    Message
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

div.messageList {
  padding: 10px;
  background-color: #eef;
}

ul {
  padding-left: 0;
}
ul li {
  list-style-type: none;
  padding: 10px;
  border: 1px solid black;
  border-radius: 6px;
  margin-bottom: 10px;
  max-width: 500px;
  background-color: lightblue;
}
</style>
