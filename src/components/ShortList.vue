<template>
  <div class="favourites">
    <h4 v-if="shortList.length">Your Shortlist</h4>
    <h4 v-if="!shortList.length">Click on a name to shortlist it...</h4>
    <ul>
      <li :key="shortListItem.id" v-for="shortListItem in getShortListItems()" :class="shortListItem.sex" v-text="shortListItem.name" @click="toggleShortListEntry(shortListItem.id)"></li>
    </ul>
    <hr v-if="shortList.length" />
  </div>
</template>

<script>
  export default {
    name: 'ShortList',
    props:  ['babyNames', 'shortList', 'toggleShortListEntry'],
    methods: {
      getShortListItems() {
        return this.shortList.map((shortListId) => {
          return this.babyNames.find((babyName) => {
            return babyName.id === shortListId;
          });
        });
      }
    }
  }
</script>

<style>
</style>