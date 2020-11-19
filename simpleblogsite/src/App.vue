<template>
  <div id="app">
    <h1 id="main-title">LIVE-BLOG</h1>
    <add-post />
    <view-posts />
  </div>
</template>

<script>
import ViewPosts from "./components/ViewPosts.vue";
import AddPost from "./components/AddPost.vue";

export default {
  name: "App",
  components: {
    ViewPosts,
    AddPost,
  },
};
</script>

<style>
html {
    background-color: rgb(236, 236, 236);
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: black;
  margin-top: 60px;
}
#main-title {
  font-family: "Amatic SC", cursive;
  font-size: 60px;
  font-weight: bolder;
  color: maroon;
}
</style>
