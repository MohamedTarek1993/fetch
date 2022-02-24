<template>
  <div>
      <h3 v-if="errprMsg">{{ errprMsg}}</h3>
      <div v-for="post in posts" :key="post.id">
      <h3>{{post.id}} . {{post.title}}</h3>
      <p>{{post.body}}</p>
      </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "ListPost",
  data() {
    return {
      posts: [],
      errprMsg:'',
    };
  },
  created(){
  this.gitPost()
  }
  ,
  methods: {
    gitPost() {
      axios
        .get("https://jsonplaceholder.typicode.com/posts")
        .then((response) => {
          this.posts = response.data;
        })
        .catch((error) => {
          console.log(error);
         this.errprMsg = 'Error Message';
        });
    },
  },
};
</script>

<style>
</style>