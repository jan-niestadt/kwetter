<template>
  <div>
    <p class='username'>
      <input
        ref="fieldUserName"

        type='text' 
        placeholder="Wie ben je?"
        :class="{ invalid: value.user.length === 0 }" 

        :value="value.user" 
        @input="valueChanged" />
    </p>
    <textarea 
      ref="myTextArea"

      placeholder="Wat is er aan de hand?" 
      autofocus
      :class="{ invalid: value.message.length > maxLength }" 

      @keydown.enter.exact.prevent
      @keyup.enter.exact="post"

      :value="value.message"
      @input="valueChanged" 
      ></textarea>
    <button @click="post" :disabled="!canPostMessage">Verstuur</button>
  </div>
</template>

<script>
export default {

  // Waardes die dit component ontvangt van de parent.
  // Niet wijzigen in dit component!
  props: {
    value: Object,
    maxLength: Number,
    placeholderText: String
  },

  // Dynamisch berekende props
  computed: {

    // Kan het bericht geplaatst worden, of niet? (leeg, te lang of geen naam gegeven)
    canPostMessage: function () {
      return this.value.user.length > 0 && this.value.message.length > 0 && this.value.message.length <= this.maxLength;
    }

  },

  // Methods die je bijv. kunt aanroepen in reactie op events
  methods: {

    // Wordt aangeroepen als de Verstuur knop ingedrukt wordt
    post: function () {
      if (this.canPostMessage) {
        // Stuur het "post-message" event dat onze parent afhandelt door het bericht te plaatsen
        this.$emit('post-message');
        // Zet de focus
        this.$refs.myTextArea.focus();
      }
    },

    // Wordt aangeroepen als de waarde van user of message verandert
    valueChanged: function () {
      this.$emit('input', {
        user: this.$refs.fieldUserName.value,
        message: this.$refs.myTextArea.value
      });
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
div {
  padding: 10px;
}

input, textarea {
  padding: 6px;
  border: 2px solid #aaf;
  border-radius: 4px;
  font-size: 14pt;
}

textarea {
  width: 14cm;
  height: 2cm;
}

.invalid {
  background-color: #fdd;
}

button {
  font-size: 12pt;
  margin-top: 10px;
}
</style>
