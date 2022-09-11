<template>
  <div>
      video search component
    <SearchInput @newTerm = "handleNewTerm" ></SearchInput>
    <Videos v-bind:videos="videos"></Videos>
    <!-- {{videos.valueOf()}} -->
  </div>
</template>

<script lang="ts">
  import SearchInput from "./components/icons/searchInput.vue";
  import Videos from './components/icons/Videos.vue';
  const API_KEY = "29728459-be7369863faf03b8e8b937ccb";
  
  export default{
    name: 'App',
    components:{
    SearchInput,
    Videos,
    },
    data() {
    return {
      videos  : [] as String[],
    };
  },
  methods: {
    async handleNewData(searchInput) {
      const response = await fetch(
        "https://pixabay.com/api/videos/?" +
          new URLSearchParams({
            key: API_KEY,
            q: searchInput,
          })
      );
      const data = await response.json();
      this.videos = data.hits as String[];
    }
  }
}
</script>

<style>
</style>
