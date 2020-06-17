<template lang="html">
  <div>
    <li v-on:click="handleClick">{{country.name}}</li>
  </div>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: 'list-item',
  props: ['country'],
  methods: {
    handleClick(){
      eventBus.$emit('selected-country', this.country)
    }
  }
}
</script>

<style lang="css" scoped>
li {
  list-style: none
}
</style>
