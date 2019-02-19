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
    </template>
    <template v-if='step === 3' >

    </template>
   
   

  </div>
</template>

<script>

import PostComponent from './PostComponent';


export default {
  name: 'BodyComponent',
  props: {
    step: Number,
    posts: Array,
    filters: Array,
    image: String,
    selectedFilter: String,
  },
  components:{
      "post" : PostComponent
  }
}
</script>

<style lang="scss" src="../styles/body.scss">
</style>
