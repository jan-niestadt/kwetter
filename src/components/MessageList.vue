<template>
  <ul>
    <Message v-for="(message, index) in messages.slice().reverse()" :message="message" :index="index" :key="index" />
  </ul>
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

ul {
  padding: 0 10px 10px 10px;
}
</style>
