<template>
    <li class="list-group-item media" @click="onVideoSelect">
        <img class="mr-3" :src="thumbailUrl" alt="">
        <div class="media-body">
        {{ itemVideo.snippet.title }}
        </div>
        </li>
</template>

<script>
export default {
    name: 'VideoListItem',
    props: ['itemVideo'],
    methods: {
        onVideoSelect: function(){
            this.$emit('videoSelect', this.itemVideo)
        }
    },
    computed: {
        thumbailUrl: function() {
            return this.itemVideo.snippet.thumbnails.default.url
        }
    }
}
</script>

<style scoped>
li {
    display: flex;
    cursor: pointer;
}
li:hover {
    background-color: #eee;
}
</style>
