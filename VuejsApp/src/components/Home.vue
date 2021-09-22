<template>
  <div class="home">
    <h1>{{ object }}</h1>
    <p>Welcome to your new single-page application, built with <a href="https://vuejs.org" target="_blank">Vue.js</a>.
    </p>
    <button @click="get()">tıkla</button>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Home',
  data() {
    return {
      object: []
    }
  },
  props: {
    msg: String
  },
  methods: {
    get() {
      console.log('axios')
      axios.create({
        baseURL: "c_webapi:8099"
      }).get("/WeatherForecast").then(r => {
        this.object = r.data
      })
    }
  },
  created() {
    this.get();
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>

