<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
  </div>
  <div id="app-5">
    <p>{{ message }}</p>
    <button v-on:click="reverseMessage">Reverse Message</button>
  </div>
  <div id="app">
      <p>{{ message }}</p>
      <button v-on:click="reverseMessage">Reverse Message</button>
      <p>
          <input v-model="kafmessage" placeholder="Enter Kafka Message" />
          <button v-on:click="sendkafmessagefunction">Send Message</button>
          <p>Message is: {{ kafmessage }}</p>
      </p>
      
    </div>
</template>

<script>
var kaf = require("./producer.js");

var Kafka = kaf();
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data: function () {
    return {
      message: "Hello Vue.js!",
      kafmessage: "kaf-message",
    };
  },

  methods: {
    reverseMessage: function () {
      this.message = this.message.split("").reverse().join("");
    },
    sendkafmessage: function () {},
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
