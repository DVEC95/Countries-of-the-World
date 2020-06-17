<template lang="html">
  <div v-if="country">
    <ul>
      <h3>{{country.name}}</h3>
      <h4 v-if="country.nativeName !== country.name">({{country.nativeName}})</h4>
      <li v-if="country.capital">Capital: {{country.capital}}</li>
      <li>Population: {{country.population | formatNumber}}</li>
      <li>Spoken Language: {{country.languages[0].name}} ({{country.languages[0].nativeName}})</li>
      <li v-if="country.region && country.subregion">Region: {{country.region}} ({{country.subregion}})</li>
      <li v-if="country.region && !country.subregion">Region: {{country.region}}</li>
      <br>
      <img :src=country.flag alt="Country Flag" height="200">
    </ul>
  </div>
</template>

<script>
export default {
  name: 'country-detail',
  props: ['country'],
  filters: {
    formatNumber: function(number){
      let parts = number.toString().split(".");
      parts[0] = parts[0].replace(/\B(?=(\d{3})+(?!\d))/g, ",");
      return parts.join(".");
    }
  }
}
</script>

<style lang="css" scoped>
ul {
  font-family: Helvetica, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2E8B57;
  margin-top: 20px;
}

li {
  list-style: none
}

img {
  border:2px solid black;
}

h3 {
  padding: 2px;
  margin-top: 2px;
  margin-bottom: 1px;
}

h4 {
  padding: 0px;
  margin-top: 0px;
  margin-bottom: 5px;
}
</style>
