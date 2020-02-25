<template>
        <ul class="list-group col-md-4">
           <VideoListItem 
           @videoSelect="onVideoSelect"
           v-for="singleVideo in videosArray" 
           :key="singleVideo.index" 
           :itemVideo="singleVideo"  
           > 
          <!-- binduje singleVideo objekat koji je dobio od parenta kroz props videosArray svom child komponenti videolistitem  -->
           </VideoListItem>
        </ul>
</template>


<script>
import VideoListItem from './VideoListItem';

export default {
    name: 'VideoList',
    methods: {
        onVideoSelect: function(itemVideo){
            this.$emit('videoSelect', itemVideo)
        }
    },
    components: {
        VideoListItem
    },
    props: {
        videosArray: Array
    }
}
</script>

<style lang="stylus">

</style>