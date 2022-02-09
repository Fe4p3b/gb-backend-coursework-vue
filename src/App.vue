<template>
  <div id="app">
    <input type="text" v-model="link" />
    <button @click.prevent="send()">send</button><br />
    <a :href="this.info">{{ info }}</a>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "App",
  components: {},
  data() {
    return {
      link: "",
      info: "",
    };
  },
  mounted() {},
  methods: {
    send() {
      const host = "https://gb-backend1-coursework.herokuapp.com";
      let data = { original_url: this.link };
      console.log(data);
      axios
        .post(host, data)
        .then((response) => {
          console.log(response);
          this.info = response.data.short_url;
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.link {
  font-size: 16px;
  line-height: 130%;
}
</style>
