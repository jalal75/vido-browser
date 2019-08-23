<template>
    <ul class="list-group col-md-4">
        <VideoListItem 
            v-for="video in videos" 
            v-bind:video="video"
            v-bind:key="video.etag"
            @videoSelect = "onVideoSelect"
        >

        </VideoListItem>
    </ul>
</template>

<script>
import VideoListItem from './VideoListItem'
export default {
    name: "VideoList",
    // props:['videos'],   or
    props:{
        videos: Array
    },
    components:{
        VideoListItem
    },
    methods:{
        onVideoSelect(video){
            this.$emit('videoSelect',video)
        }
    }
}
</script>

<style>

</style>
