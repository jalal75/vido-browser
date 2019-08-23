<template>
    <div class="col-md-8" v-if="video">
        <div class="embed-responsive embed-responsive-16by9">
            <iframe class="embed-responsive-item" :src="videoUrl" />
        </div>
        <div class="details">
            <h4>{{this.video.snippet.title}}</h4>
            <p>{{ this.video.snippet.description }}</p>
        </div>
    </div>
</template>
<script>
export default {
    name:"VideoDetal",
    props:['video'],
    computed: {
        videoUrl(){
            const videoId = this.video.id.videoId
            //or
            // const { videoId } = this.video.id
            return `https://www.youtube.com/embed/${videoId}`
        }
    }
}
</script>
<style scoped>
    .details{
        margin-top: 10px;
        padding: 10px;
        border: 1px solid #ddd;
        border-radius: 4px;
    }
</style>

