<template>
  <div>
    <h1>Blog</h1>
    <div v-for="post in posts" :key="post.id">
      <h3>{{post.title}}</h3>
      <p>{{post.excerpt}}</p>
    </div>
  </div>
</template>
<script>
import Vue from 'vue'
import VueCookies from 'vue-cookies'
Vue.use(VueCookies)
export default {
  data() {
    return {
      posts: [],
    };
  },
  created() {
    const token = $cookies.get('token');
    const url = `/api/v1/post?api_token=${token}`;
    axios.get(url).then(response => {
      this.posts = response.data.data;
    });
  }
};
</script>