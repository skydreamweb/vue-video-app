<template>
    <div v-if="itemVideo" class="col-md-8">
        <div class="embed-responsive embed-responsive-16by9">
            <iframe class="embed-responsive-item" :src="videoUrl" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
        </div>
        <div class="details">
       <h4> {{ itemVideo.snippet.title }}</h4>
       <p>{{ itemVideo.snippet.description }}</p>
    </div>
    </div>
</template>

<script>
export default {
    name: 'VideoDetail',
    props: ['itemVideo'],
    computed: {
        videoUrl: function() {
        const videoId = this.itemVideo.id.videoId;
        return 'https://www.youtube.com/embed/' + videoId;
        }
    }
}
</script>

<style scoped>
.details {
    margin-top: 10px;
    padding: 10px;
    border: 1px solid black;
    border-radius: 4px;
}
</style>