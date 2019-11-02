<template>
  <div id="app">
    <PostForm />
    <hr>
    <p>{{postsCount}}</p>
    <div class="post" v-for="post in validPosts" :key="post.id">
      <h2>{{post.title}}</h2>
      <p>{{post.body}}</p>
      <hr>
    </div>
  </div>
</template>

<script>
import {mapGetters, mapActions} from 'vuex'
import PostForm from '@/components/PostForm'
export default {
  name: 'app',
  components: {
    PostForm
  },
  computed: mapGetters(['validPosts', 'postsCount']),
  methods: mapActions(['fetchPosts']),
  async mounted() {
    this.fetchPosts(10);
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
