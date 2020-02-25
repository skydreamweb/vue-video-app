<template>

<div class="container">
  <SearchBar @termChange="onTermChange"></SearchBar>
  <div class="row">
  <VideoDetail :itemVideo="selectedVideo"></VideoDetail>
  <VideoList @videoSelect="onVideoSelect" :videosArray="videos"></VideoList>
  </div>
</div>

</template>

<script>

import axios from 'axios';
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
import VideoDetail from './components/VideoDetail';

const API_KEY = 'AIzaSyANrsm43eJ5IRGuxfuw8ffqaGxX7RQxOus';


export default {

  name: 'App',
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },

  data() {
    return {
      videos: [],
      selectedVideo: null
    }
  },

  methods: {
    onVideoSelect: function(itemVideo){
      this.selectedVideo = itemVideo;
      
    },
    onTermChange: function (searchTerm) { // searchTerm drugi argument funkcije onInput iz SearchBar.vue (event.target.value)
   
     axios.get('https://www.googleapis.com/youtube/v3/search', {
       params: {
         key: API_KEY,
         type: 'video',
         part: 'snippet',
         q: searchTerm // query for our searchTerm
       }
     }).then(response => {
       this.videos = response.data.items // Dodaje svaki video items u array videos unutar Data
     })
     .catch(error => {
    console.log(error.response)
});
      
    }
  }
}
</script>




<style>

</style>
