<template>
  <div class="message-input">
    <textarea v-model="message" :class="{ tooLong: message.length > maxLength }"></textarea>
    <p><button v-on:click="post" :disabled="message.length > maxLength">Verstuur</button></p>
    <p><b>Lengte:</b> {{ message.length }} / {{ maxLength }}
    (<span v-if="message.length <= maxLength">nog {{ maxLength - message.length}} tekens over</span>
     <span v-else>{{ message.length - maxLength }} tekens teveel</span>)
    </p>
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
  },

  mounted: function () {
    this.$nextTick(function () {
      // Code that will run only after the
      // entire view has been rendered
      let el = this.$el;
      setTimeout(function() {
        el.children[0].focus(); // focus on textarea
      }, 100);
    });
  },

  methods: {
    post: function () {
      //console.log("Posting message: " + this.message);
      this.$emit('post-message', this.message);
      this.message = '';
      this.$el.children[0].focus(); // focus on textarea
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
textarea {
  width: 12cm;
  height: 2cm;
  font-size: 14pt;
  border-radius: 10px;
  padding: 10px;
}

textarea.tooLong {
  background-color: #fdd;
}

button {
  font-size: 14pt;
}
</style>
