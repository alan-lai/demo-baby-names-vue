<template>
  <form>
    <input type="text" placeholder="Type to filter.." @input="updateKeyword($event.target.value)" />
  </form>
</template>

<script>
  export default {
    name: 'Search',
    props: ['updateKeyword']
  }
</script>

<style>
</style>