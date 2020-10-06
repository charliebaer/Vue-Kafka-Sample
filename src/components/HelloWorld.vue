<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
  </div>
  <!--
  <div id="app-5">
    <p>{{ message }}</p>
    <button v-on:click="reverseMessage">Reverse Message</button>
  </div>
  -->
  <div id="app">
    <!-- <p>{{ message }}</p>
    <button v-on:click="reverseMessage">Reverse Message</button>              -->

    <p></p>
    <input v-model="kafmessage" placeholder="Enter Kafka Message" />
    <button v-on:click="sendkafmessage">Send Message</button>
    <!--   <button v-on:click="postfunction">Send Message</button> -->
  </div>
</template>


<script>
  import axios from "axios";
  export default {
    name: "HelloWorld",
    props: {
      msg: String,
    },
    data: function () {
      return {
        message: "Hello Vue.js!",
        kafmessage: null,
        info: null  //delete this garbage!!!!
      };
    },
    methods: {
      reverseMessage: function () {
        this.message = this.message.split("").reverse().join("");
      },


      sendkafmessage: function () {
        // var kafevent = this.kafmessage;        //don't delete function
        var message = this.kafmessage;
        alert(message);
        axios
          .post(`http://localhost:3000/${message}`);
      },


    },
    /*
    postfunction: function () {
      // var kafevent = this.kafmessage;
      axios
        .get('https://api.coindesk.com/v1/bpi/currentprice.json')
        .then(response => (this.info = response.data.bpi))
        .catch(error => console.log(error));
      var message = this.info;
      alert(message);

    },
    */
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