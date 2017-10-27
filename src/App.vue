<template>
  <div id="app">
    <app-header></app-header>
    <app-search-bar></app-search-bar>
    <hr>
    <app-video-details></app-video-details>
    <hr>
    <app-video-list></app-video-list>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import SearchBar from './components/SearchBar.vue';
import VideoList from './components/VideoList.vue';
import VideoDetails from './components/VideoDetails.vue';

import { searchBus } from './main';
export default {
  
  data () {
    return {
      term: '',
      videos: []
    }
  },
  components: {
    appHeader: Header,
    appSearchBar: SearchBar,
    appVideoDetails: VideoDetails,
    appVideoList: VideoList
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  color: #2c3e50;
  
}

h1, h2 {
  font-weight: normal;
}

a {
  color: #42b983;
}
</style>
