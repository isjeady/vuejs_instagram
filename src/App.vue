<template>
  <div id="app">
    <div class="app-phone">
      <div class="header">
        <img alt="Vue logo" src="./assets/logo.png" width="60px">
      </div>
     
      <body-component :posts='posts' :filters='filters' />
      
      <div class="footer">
        <div class="home-icon">
          <i class="fas fa-home fa-lg"></i>
        </div>
        <div class="upload-icon">
          <i class="far fa-plus-square fa-lg"></i>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import BodyComponent from './components/BodyComponent.vue'

import posts from './data/posts';
import filters from './data/filters';

export default {
  name: 'app',
  data() {
    return {
      posts,
      filters,
    };
  },
  components: {
    "body-component" : BodyComponent
  }
}
</script>

<style lang='scss' src='./styles/app.scss'>
</style>
