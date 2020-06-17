<template lang="html">
    <option :value="country">{{country.name}}</option>
</template>

<script>
export default {
  name: 'list-item',
  props: ['country']
}
</script>

<style lang="css" scoped>
li {
  list-style: none
}
</style>
