<template>
  <div class="message-input">
    <textarea v-model="message"></textarea>
    <p><b>Je bericht:</b> {{ message }}</p>
    <p><b>Lengte van je bericht:</b> {{ message.length }}</p>
    <p><b>Letters over:</b> {{ 140 - message.length }}</p>
    <p><b>Aantal woorden:</b> {{ numberOfWords }}</p>
  </div>
</template>

<script>
export default {

  // Values this component receives from its parent
  // Don't change these inside the component!
  props: {
    // Initial value for our data property
    initialMessage: String
  },

  // Internal variables for this component
  data: function () {
    return {
      message: this.initialMessage // initialized from prop
    }
  },

  // Dynamically calculate a property
  computed: {
    numberOfWords: function () {
      return this.message.trim().split(/\s+/).length;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
textarea {
  width: 15cm;
  height: 3cm;
  font-size: 14pt;
  border-radius: 10px;
  padding: 10px;
}
</style>
