<template>
  <form @submit.prevent="createPost">
    <div>
      <label for="userId"> User Id</label>
      <input type="text" id="userId" ref="inputRefs" v-model="formData.userid" />
    </div>
    <div>
      <label for="title"> Title Post</label>
      <input type="text" id="title" ref="inputRef2" v-model="formData.title" />
    </div>
    <div>
      <label for="body">Body Post</label>
      <input type="text" id="body" ref="inputRef" v-model="formData.body" />
    </div>
    <button>Create Post</button>
  </form>
</template>

<script>
import axios from "axios";
export default {
  name: "CreatePost",
  data() {
    return {
      formData: {
        userid: "",
        title: "",
        body: "",
      },
    };
  },
  mounted(){
      this.$refs.inputRef.focus();
   
  },
  methods: {
    createPost() {
      axios
        .post("https://jsonplaceholder.typicode.com/posts", this.formData)
        .then((response) => console.log(response))
        .catch((error) => {
          console.log(error);
          //   this.errprMsg = "Error Message";
        });
    },
  },
};
</script>

<style>
</style>