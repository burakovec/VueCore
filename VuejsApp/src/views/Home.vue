<template>
  <div>
    <b-card title="Kick start your project 🚀">
      <b-card-text>All the best for your new project.</b-card-text>
      <b-card-text>Please make sure to read our
        <b-link
            href="https://pixinvent.com/demo/vuexy-vuejs-admin-dashboard-template/documentation/"
            target="_blank"
        >
          Template Documentation
        </b-link>
        to understand where to go from here and how to use our template.
      </b-card-text>
    </b-card>

    <b-card title="Want to integrate JWT? 🔒">
      <b-card-text>We carefully crafted JWT flow so you can implement JWT with ease and with minimum efforts.
      </b-card-text>
      <b-card-text>Please read our JWT Documentation to get more out of JWT authentication.</b-card-text>
    </b-card>
    <b-button
        type="submit"
        variant="primary"
        block
        @click="getWeforecast"
    >
      İstek Yolla
    </b-button>
    <b-card title="🔒">
      <b-card-text v-for="(item,i) in content" :key="i">{{ item }}</b-card-text>
    </b-card>
  </div>
</template>

<script>
import {
  BCard, BCardText, BLink, BButton,
} from 'bootstrap-vue'

export default {
  components: {
    BCard,
    BCardText,
    BLink,
    BButton,
  },
  data() {
    return {
      content: [],
    }
  },
  methods: {
    async getWeforecast() {
      let axios = require('axios');

      let config = {
        method: 'get',
        url: 'http://localhost:8099/WeatherForecast',
        headers: {
          'Access-Control-Allow-Origin': '*'
        }
      };
      let response = await axios(config)
      this.content = response.data
    },
  },

}
</script>

<style>

</style>
