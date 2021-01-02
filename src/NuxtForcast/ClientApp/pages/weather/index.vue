<template>
  <div>
    <b-table hover striped v-cloak :items="weather"></b-table>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import axios from 'axios'

export default Vue.extend({
  data: () => ({
    loading: false,
    weather: [],
  }),
  created() {
    this.getWeather()
  },
  methods: {
    getWeather() {
      this.$nextTick(async () => {
        this.$nuxt.$loading.start()

        const promis = await axios
          .get('https://localhost:5001/weatherforecast')
          .then((resp) => {
            this.weather = resp.data
            this.$nuxt.$loading.finish()
          })
      })
    },
  },
})
</script>

<style>
[v-cloak] {
  visibility: none;
}
</style>