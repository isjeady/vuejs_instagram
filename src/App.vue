<template>
  <div id="app">
    <div class="app-phone">
      <div class="header">
        <img alt="Vue logo" src="./assets/logo.png" width="60px">
      </div>
     
      <body-component 
        :posts='posts' 
        :filters='filters' 
        :step='step'
        :image='image'
        :selectedFilter='selectedFilter'
      />
     
      <div class="footer">
        <div class="home-icon">
          <i class="fas fa-home fa-lg"></i>
        </div>
        <div class="upload-icon">
           <input type='file'
            name='file'
            id='file'
            class='inputfile'
            @change='uploadImage'
            :disabled='step !== 1'
          />
          <label for='file'>
            <i class="far fa-plus-square fa-lg"></i>
          </label>
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
      step: 1,
      posts,
      filters,
      image : '' ,
      selectedFilter: '',
    };
  },
  methods: {
    uploadImage(evt) {
      const files = evt.target.files;
      if (!files.length) return;

      const reader = new FileReader();
      reader.readAsDataURL(files[0]);
      reader.onload = (readerEvt) => {
        this.image = readerEvt.target.result;
        this.step = 2;
      };

      // To enable reuploading of same files in Chrome
      document.querySelector('#file').value = '';
    },
  },
  components: {
    "body-component" : BodyComponent
  }
}
</script>

<style lang='scss' src='./styles/app.scss'>
</style>
