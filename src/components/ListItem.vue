<template lang="html">
<div >
  <ul>
  <li>{{movie.title}}</li>
  </ul>
  </div>
</template>

<script>

export default {
  name: 'list-item',
  props: ['movie'],
}
</script>

<style lang="css" scoped>
</style>
