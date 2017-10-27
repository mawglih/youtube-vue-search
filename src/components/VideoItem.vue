<template>
    <div>
        <li class="list-group-item" @click="onSelect">
            

            <div >
                <div class="video-list media">
                <img class="align-self-start mr-3" :src="video.url" :alt="video.title" />
                <div class="media-body">
                    <h5 class="mt-0">{{video.title}}</h5>
                    <p>{{video.description}}</p>
                    
                </div>
                </div>
                </div>
        </li>
        
    </div>

</template>
<script>
import { searchBus } from '../main';
export default {
    data() {
        return {
            selectedVideo: null
        }
    },
    props: ['video'],
    methods: {
        onSelect() {
            this.selectedVideo = this.video;
            console.log('item: ', this.selectedVideo);
            searchBus.$emit('SelectedVideo', this.selectedVideo);
        }
    }

}

</script>
<style>

</style>