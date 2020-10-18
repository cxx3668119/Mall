<template>
  <div id="app">
    <router-view></router-view>
  </div>
</template>

<script>
import axios from "axios"; // eslint-disable-line no-unused-vars
export default {
  name: "App",
  components: {},
  data() {
    return {
      res: {},
    };
  },
  mounted() {
    this.axios.get("/mock/user/login.json").then((res) => {
      this.res = res;
    });
  },
};
</script>

<style>
</style>
