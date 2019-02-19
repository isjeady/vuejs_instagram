<template>
  <div class="body">
    <div class='feed' v-dragscroll.y>
      <div v-for='post in posts' :key="'post_' + posts.indexOf(post)">
          <post :post='post' />
      </div>
    </div>
   

  </div>
</template>

<script>

import PostComponent from './PostComponent';


export default {
  name: 'BodyComponent',
  props: {
    msg: String,
    posts: Array,
    filters: Array,
  },
  components:{
      "post" : PostComponent
  }
}
</script>

<style lang="scss" src="../styles/body.scss">
</style>
