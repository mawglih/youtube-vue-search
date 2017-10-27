<template>
  <div>
      <div class="row">
          <div class="col-sm-10 offset-sm-1">
            <div class="input-group">
            <input type="text" class="form-control" v-model="search" placeholder="Search for youtube video." aria-label="Search for youtube video">
            <span class="input-group-btn">
                <button class="btn btn-warning" @click.prevent="onSelect" type="button">Go!</button>
            </span>
            </div>
        </div>
      </div>
  </div>
</template>

<script>
import { searchBus } from '../main';
import Youtube from '../utils/Youtube';
export default {
    data() {
        return{
            search: '',
            videos: []
        }
    },
    methods: {
        onSelect: function() {
            Youtube.search(this.search)
            .then(videos => {
                this.videos = videos;
                console.log('searchbar videos', this.videos);
                searchBus.$emit('getVideos', this.videos);
            });

            
            this.search = '';
        }
    }
}
</script>
    
    
<style>

</style>
