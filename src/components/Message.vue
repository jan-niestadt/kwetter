<template>
  <li><b>{{ message.user }}</b><span class='time-ago'>{{ timeAgo }}</span><br/>{{ message.message }}</li>
</template>

<script>
export default {

  // Values this component receives from its parent
  // Don't change these inside the component!
  props: {
    // Initial value for our data property
    message: Object,
    index: Number
  },

  computed: {
    timeAgo: function () {
      let s = Math.floor( ((new Date()).getTime() - this.message.time.getTime()) / 1000 );
      if (s < 20)
        return `zojuist`;
      if (s < 60)
        return `minder dan een minuut geleden`;
      if (s < 3600)
        if (s < 120)
          return `1 minuut geleden`;
        else
          return `${Math.floor(s / 60)} minuten geleden`;
      return `${Math.floor(s / 3600)} uur geleden`;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
li {
  list-style-type: none;
  padding: 10px;
  border: 1px solid #ddf;
  border-radius: 3px;
  background-color: #fff;
  margin-bottom: 5px;
}

.time-ago {
  margin-left: 10px;
  font-size: 80%;
  color: #888;
}

</style>
