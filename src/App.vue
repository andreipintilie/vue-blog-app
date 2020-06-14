<template>
  <div id="app">
    <Navbar />
    <b-container>
      <WritePost @add-post="addPost" />
      <Posts :posts="postdata" @remove-post="removePost" />
    </b-container>
  </div>
</template>

<script>
import "bootstrap/dist/css/bootstrap.css";
import "bootstrap-vue/dist/bootstrap-vue.css";

import Navbar from "./components/Navbar.vue";
import WritePost from "./components/WritePost.vue";
import Posts from "./components/Posts";

export default {
  name: "App",
  data() {
    return {
      postdata: [
        {
          title: "",
          content: "",
          category: null,
          tags: []
        }
      ]
    };
  },
  components: {
    Navbar,
    WritePost,
    Posts
  },
  methods: {
    addPost: function(value1, value2, value3, value4) {
      this.postdata.push({
        title: value1,
        content: value2,
        category: value3,
        tags: value4
      });
      this.postdata.title = "";
      this.postdata.content = "";
      this.postdata.category = null;
      this.postdata.tags = [];
    },
    removePost: function(index) {
      this.postdata.splice(index, 1);
    }
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Montserrat&display=swap");

* {
  margin: 0;
  outline: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background: #f0f0f0 !important;
  font-family: "Montserrat", sans-serif;
}
</style>
