<template lang="html">
  <div>
    <select v-model="selectedCountry" v-on:change="handleSelect">
      <list-item v-for="(country, index) in countries" :country="country" :key="index"></list-item>
    </select>
  </div>
</template>

<script>
import ListItem from './ListItem.vue';
import { eventBus } from '../main.js'

export default {
  name: 'countries-list',
  props: ['countries'],
  methods: {
    handleSelect(){
      eventBus.$emit('selected-country', this.selectedCountry)
    }
  },
  components: {
    "list-item": ListItem
  },
  data(){
    return {
      selectedCountry: null
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
</style>
