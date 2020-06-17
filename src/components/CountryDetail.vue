<template lang="html">
  <div v-if="country">
    <ul>
      <h3>{{country.name}}</h3>
      <li>({{country.nativeName}})</li>
      <li>Capital: {{country.capital}}</li>
      <li>Population: {{country.population | formatNumber}}</li>
      <li>Spoken Language: {{country.languages[0].name}} ({{country.languages[0].nativeName}})</li>
      <li>Region: {{country.region}} ({{country.subregion}})</li>
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
</style>
