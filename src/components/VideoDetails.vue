<template>
    <div>
        <div v-if="selectedVideo">
            <div class="col-md-8">
                <div class="embed-responsive embed-responsive-16by9">
                    <iframe className="embed-responsive-item" :src="url+videoId"></iframe>
                </div>
                <div class="details">
                    <div>{{selectedVideo.title}}</div>
                    <div>{{selectedVideo.description}}</div>
                </div>
            </div>
        </div>
        <div v-else>
            Loading .....
        </div>
    </div>

</template>
<script>
import { searchBus } from '../main';
export default {
    data() {
        return {
            selectedVideo:null,
            videoId:'',
            url:'https:/www.youtube.com/embed/'
        }
    },
    created() {
        searchBus.$on('getVideos', (data) => {
            this.selectedVideo = data[0];
            this.videoId= this.selectedVideo.id;
        });
    },
    changed() {
        searchBus.$on('SelectedVideo', (data) => {
            this.selectedVideo = data;
            this.videoId= this.selectedVideo.id;
            
        })
    }
}
</script>
<style>

</style>