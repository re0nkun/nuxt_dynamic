<template>
  <div>
    <nuxt/>
    
    <ul>
      <li v-for="post in posts" :key="post.id">
        <!-- <nuxt-link :to="`/post/${post.id}`">
          {{post.title}}
        </nuxt-link> -->

        <!-- <router-link :to="{name:'post-id',params:{id: post.id}}"> -->
          {{post.title}}
        <!-- </router-link> -->
      </li>
    </ul>
  </div>
</template>

<script>
// import Logo from '~/components/Logo.vue'
import axios from 'axios'

export default {
  // layout: 'mypage',
  // components: { Logo },
  data() { 
    return {
      posts: null
    } 
  },
  mounted() {
    axios.get("https://jsonplaceholder.typicode.com/posts")
    .then(result => {
      this.posts = result.data
    })
  },
  // computed: {
  //   posts() {
  //     return this.$store.getters.posts
  //   }
  // },
  // mounted() {
  //   this.$store.dispatch("load")
  // }
}
</script>

<style>
.page-enter-active, .page-leave-active {
  transition: opacity .2s;
}
.page-enter, .page-leave-to {
  opacity: 0;
}

.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 80px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
