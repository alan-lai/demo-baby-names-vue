<template>
  <ul v-if="getNames().length"> 
    <li :key="babyName.id" v-for="babyName in getNames()" :class="babyName.sex" @click="toggleShortListEntry(babyName.id)">{{ babyName.name }}</li>
  </ul>
</template>

<script>
  export default {
    name: 'NameList',
    props: ['babyNames', 'shortList', 'toggleShortListEntry', 'keyword'],
    data() {
      return {
        nameList: []
      }
    },
    methods: {
      getNames() {
        let keywordPattern = new RegExp(this.keyword, 'i');
        return this.babyNames.filter((babyName) => {
          return babyName.name.match(keywordPattern);
        }).filter((babyName) => {
          return this.shortList.indexOf(babyName.id) < 0;
        });
      }
    }
  }
</script>

<style>
</style>