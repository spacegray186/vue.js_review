<template>
  <div>
    <input type="search" @keyup="checkEnter($event)" v-model="searchText">
    <hr>
    <input type="search" @keyup.enter="doSearch" v-model="searchText">
    <button @click="doSearch">조회</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      searchText: ''
    }
  },
  methods: {
    doSearch() {
      alert(this.searchText)
    },
    checkEnter(event) {
      // alert(event)
      if (event.keyCode === 13) {
        // alert()
        this.doSearch()
      }
    }
  }
}
</script>
