<template>
  <div class="message-input">
    <textarea v-model="message"></textarea>
    <p><b>Je bericht:</b> {{ message }}</p>
    <p><b>Lengte:</b> {{ message.length }} / {{ maxLength }} (nog {{ maxLength - message.length}} tekens over)</p>
    <p><b>Aantal woorden:</b> {{ numberOfWords }}</p>
  </div>
</template>

<script>
export default {

  // Values this component receives from its parent
  // Don't change these inside the component!
  props: {
    // Initial value for our data property
    maxLength: Number,
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
      let m = this.message.trim();
      if (m.length === 0)
        return 0;
      return m.split(/\s+/).length;
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
