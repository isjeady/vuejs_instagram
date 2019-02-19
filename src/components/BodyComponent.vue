<template>
  <div class="body">
    <template v-if='step === 1' >
         <div class='feed' v-dragscroll.y>
            <div v-for='post in posts' :key="'post_' + posts.indexOf(post)">
                <post :post='post' />
            </div>
        </div>
    </template>
    <template v-if='step === 2' >
        <div class='selected-image'
          :class='selectedFilter'
          :style="{ backgroundImage: 'url(' + image + ')' }">
        </div>
      <div class='filter-container' v-dragscroll.x>
        <filter-type v-for='filter in filters'
          :filter='filter'
          :image='image'
          :key='filters.indexOf(filter)'>
        </filter-type>
      </div>
    </template>
    <template v-if='step === 3' >

    </template>
   
   

  </div>
</template>

<script>

import filters from '../data/filters';
import PostComponent from './PostComponent';
import FilterTypeComponent from './FilterTypeComponent';
import EventBus from '../event-bus';


export default {
  name: 'BodyComponent',
  data() {
    return {
      filters,
      selectedFilter: '',
    };
  },
  props: {
    step: Number,
    posts: Array,
    image: String,
  },
  created() {
    EventBus.$on('filter-selected', (evt) => {
      this.selectedFilter = evt.filter;
    });
  },
  components:{
      "post" : PostComponent,
      'filter-type': FilterTypeComponent,
  }
}
</script>

<style lang="scss" src="../styles/body.scss">
</style>
