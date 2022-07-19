<template>
  <h2>Post list</h2>
  <div>
    <div v-if="loading">
      <h2> Loading </h2>
    </div>
    <div v-else>
      <ul class="list-group list-group-flush">
        <li v-for="post in posts" :key="post.id" class="list-group-item">
          {{ post.title}}
          <span>
            {{ post.body}}
          </span>
      </li>
      </ul>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "PostList",
  data() { 
    return {
      loading: true,
      posts: [],
    };
},
async mounted() {
  var results = await axios.get("http://jsonplaceholder.typicode.com/posts");
  this.loading = false;
  this.posts = results.data;
  console.log(results);
  
  },
};
</script>
<style></style>