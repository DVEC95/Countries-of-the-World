<template lang="html">
  <div id="app">
    <h1>Countries of the World</h1>
    <countries-list :countries="countries"></countries-list>
    <country-detail :country="selectedCountry"></country-detail>
  </div>
</template>

<script>
import { eventBus } from './main.js'
import CountriesList from './components/CountriesList.vue'
import CountryDetail from './components/CountryDetail.vue'

export default {
  name: 'app',
  data(){
    return {
      countries: [],
      selectedCountry: null
    }
  },
  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
    .then(res => res.json())
    .then(countries => this.countries = countries)

    eventBus.$on('selected-country', (country) => {
      this.selectedCountry = country;
    })
  },
  components: {
    "countries-list": CountriesList,
    "country-detail": CountryDetail
  }
}
</script>

<style lang="css" scoped>
#app {
  font-family: Helvetica, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2F4F4F;
  margin-top: 20px;
}
</style>
