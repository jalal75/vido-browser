<template>
    <div class="container">
        <SearchBar @termChange= "onTermChange"></SearchBar>
        <div class="row">
            <VideoDetal :video="selectedVideo" ></VideoDetal>
            <VideoList @videoSelect="onVideoSelect" v-bind:videos="videos"></VideoList>
        </div>
        
    </div>
</template>

<script>
import SearchBar from './components/SearchBar'
import axios from 'axios'
import VideoList from './components/VideoList'
import VideoDetal from './components/VideoDetal'
const API_KEY = "AIzaSyDC7WNvXId12xLdrOPLbDEQTGS98aasS4Q"
export default {
    name: 'App',
    components:{
        SearchBar,
        VideoList,
        VideoDetal
    },
    data: function(){return{videos:[], selectedVideo:null}},
    methods:{
        onTermChange(searchText){
            axios.get('https://www.googleapis.com/youtube/v3/search',{
                params: {
                    q: searchText,
                    part: "snippet",
                    key: API_KEY,
                    maxResults: "10",
                    pageToken: "",
                    type:"video"
                },
            }).then(res => this.videos = res.data.items)
            
        },
        onVideoSelect(video){
            this.selectedVideo = video;
        }
    }
}
</script>
