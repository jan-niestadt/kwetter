<template>
  <div class="message-input">
    <p class='username'><input type='text' v-model="name" :class="{ invalid: name.length === 0 }" placeholder="Wie ben je?" /></p>
    <textarea 
      ref="myTextArea"
      v-model="message" 
      :class="{ invalid: message.length > maxLength }" 
      :placeholder="placeholderText" 
      autofocus
      @keydown.enter.exact.prevent
      @keyup.enter.exact="post"
      ></textarea>
    <p>
      <button @click="post" :disabled="canPostMessage === false">Verstuur</button>
      ({{ numberOfWords }} woorden, {{ message.length }} / {{ maxLength }} tekens ({{ messageLengthComment }})
    </p>
  </div>
</template>

<script>
export default {

  // Values this component receives from its parent
  // Don't change these inside the component!
  props: {
    // Initial value for our data property
    maxLength: Number,
    placeholderText: String
  },

  // Internal variables for this component
  data: function () {
    return {
      message: "",
      name: ""
    }
  },

  // Dynamically calculate a property
  computed: {

    messageLengthComment: function () {
      if (this.message.length <= this.maxLength)
        return `nog ${this.maxLength - this.message.length} tekens over`;
      if (this.message.length < this.maxLength * 1.5)
        return `${this.message.length - this.maxLength} tekens teveel`;
      return `Hee, rustig aan, Dostoevsky!`;
    },

    numberOfWords: function () {
      let m = this.message.trim();
      if (m.length === 0)
        return 0;
      return m.split(/\s+/).length;
    },

    canPostMessage: function () {
      return this.name.length > 0 && this.message.length > 0 && this.message.length <= this.maxLength;
    }

  },

  mounted: function () {

/*
    this.$nextTick(function () {
      // Code that will run only after the
      // entire view has been rendered
      this.$refs.myTextArea.focus(); // focus on textarea
    });
    */

  },

  methods: {
    post: function () {
      if (this.canPostMessage) {
        //console.log("Posting message: " + this.message);
        this.$emit('post-message', {
          user: this.name,
          message: this.message,
          time: (new Date()).getTime()
        });
        this.message = '';
        this.$el.children[1].focus(); // focus on textarea
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.message-input {
  padding: 10px;
}

p.username {
  font-size: 14pt;
}

p.username input {
  padding: 6px;
  border: 2px solid #aaf;
  border-radius: 4px;
}

p.username input {
  font-size: 14pt;
}

textarea {
  width: 14cm;
  height: 2cm;
  font-size: 14pt;
  border: 2px solid #aaf;
  border-radius: 4px;
  padding: 6px;
}

.invalid {
  background-color: #fdd;
}

button {
  font-size: 12pt;
}
</style>
