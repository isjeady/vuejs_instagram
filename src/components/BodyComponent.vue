<template>
  <div class="body">
    <h1>{{ msg }}</h1>
    <div v-for='post in posts' :key='posts.indexOf(post)'>
        {{ post.username }}
        {{ post.filter }}
    </div>
    <div v-for='f in filters' :key='filters.indexOf(f)'>
        {{ f.name }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'BodyComponent',
  props: {
    msg: String,
    posts: Array,
    filters: Array,
  },
  components:{

  }
}
</script>

<style lang="scss" src="../styles/body.scss">
</style>
