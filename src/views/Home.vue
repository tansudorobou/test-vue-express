<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <!-- <HelloWorld msg="Welcome to Your Vue.js App" /> -->
    <HelloWorld v-bind:msg="message" />
  </div>
</template>

<script>
// @ is an alias to /src(
import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "Home",
  components: {
    HelloWorld
  },
  computed: {
    message() {
      const req = new XMLHttpRequest();
      let message = "";
      req.open("GET", "/foo", false);
      req.onload = function() {
        message = JSON.parse(req.responseText).msg;
      };
      req.send(null);
      return message;
    }
  }
};
</script>
