<template>
    <div >
        <ul v-for="video in videos" :key="video.id" class="list-group">
            <app-video-item :video="video"></app-video-item>
        </ul>
        
    </div>

</template>
<script>
import VideoItem from './VideoItem.vue';
import { searchBus } from '../main';
export default {
    data() {
        return{
            videos: []
        }
    },
    components: {
        appVideoItem: VideoItem
    },
 created() {
     searchBus.$on('getVideos', (data) => {
         if(data) {
             this.videos = data;
            console.log('videolist: '. this.videos);
         }
         
     });
 }
}
</script>
<style>

</style>