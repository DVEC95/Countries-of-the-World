<template lang="html">
  <div>
    <li>{{country.name}}</li>
  </div>
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
