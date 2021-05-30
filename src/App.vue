<template>
  <div id="app"></div>
  <PostForm />
  <h1>{{ postsCount }}</h1>
  <div class="post" v-for="post in allPosts" :key="post.id">
    <h2>{{ post.title }}</h2>
    <p>{{ post.body }}</p>
  </div>
</template>

<script>
import { mapActions, mapGetters } from 'vuex'
import PostForm from './components/PostForm'

export default {
  name: 'App',
  // computed: {
  //   allPosts() {
  //     console.log(this.$store.getters.allPosts)
  //     return this.$store.getters.allPosts;
  //   }
  // },
  computed: mapGetters(['allPosts', 'postsCount']),
  methods: mapActions(['fetchPosts']),
  components: { PostForm },
  mounted() {
    // this.$store.dispatch('fetchPosts')
    this.fetchPosts(4)
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 60px auto;
  width: 400px;
}
.post {
  border: 1px solid #ccc;
  border-radius: 5px;
  margin-bottom: 1rem;
}
</style>
