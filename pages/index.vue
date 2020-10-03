<template lang="html">
  <div>
    <div class="mor">
      Infinity
    </div>
    <div>
      <v-text-field v-model="DayID" type="text" label="Day - DD(07)" color="#B71C1C" />
      <v-text-field v-model="MonthID" type="text" label="Month - MM(03)" color="#B71C1C" />
      <v-text-field v-model="YearID" type="text" label="Year - YYYY(2000)" color="#B71C1C" />
      <v-btn color="#AB47BC" @click="kuku">
        Search
      </v-btn>
      </v-date-picker>
    </div>
    <v-divider class="mt-2 mb-2" />
    <div v-for="list in ID" :key="list.date">
      <!-- {{list}} -->
      <nuxt-link :to=" {name: 'product-id', params: { id: list }} ">
        <img
          style="max-width:100%"
          :src="list.hdurl"
        >
      </nuxt-link>
    </div>
  </div>
</template>
<script>
import axios from 'axios'
export default {
  data () {
    return {
      ID: null,
      DayID: '',
      MonthID: '',
      YearID: '',
      DateID: ''
    }
  },
  methods: {
    kuku () {
      const url = 'https://api.nasa.gov/planetary/apod?date=' + this.YearID + '-' + this.MonthID + '-' + this.DayID + '&hd=true&api_key=iK6QWVlZ9w0RUsSNWob3UL5KcXFehRlXBHvKuW6p'
      axios.get(url).then((response) => {
        this.ID = response
      })
    }
  }
}
</script>
<style lang="css" scoped></style>
