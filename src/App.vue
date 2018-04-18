<template>
  <div>
    <header>
      <Search v-bind="{updateKeyword}" />
    </header>
    <main>
      <ShortList v-bind="{babyNames, shortList, toggleShortListEntry}" />
      <NameList v-bind="{babyNames, shortList, toggleShortListEntry, keyword}" />
      <Credit />
    </main>    
  </div>
</template>

<script>
import Search from './components/Search.vue'
import ShortList from './components/ShortList.vue'
import NameList from './components/NameList.vue'
import Credit from './components/Credit.vue'
import BabyNameLibrary from './data/data';

export default {
  name: 'App',
  data () {
    return {
      babyNames: BabyNameLibrary,
      shortList: [],
      keyword: ''
    }
  },
  methods: {
    updateKeyword(newKeyword) {
      this.keyword = newKeyword;
    },
    toggleShortListEntry (id) {
      // console.log(id)
      const index = this.shortList.indexOf(id);
      if(index >= 0) {
        let newShortList = this.shortList;
        newShortList.splice(index, 1);
        // console.log(newShortList)
        this.shortList = newShortList;
      } else {
        let newShortList = this.shortList.concat([id]);
        this.shortList = newShortList;
      }
    }
  },
  components: {
    Search,
    ShortList,
    NameList,
    Credit
  }
}
</script>

<style>
</style>
