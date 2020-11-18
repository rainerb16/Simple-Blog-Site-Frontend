<template>
    <div id="app">
        <h1 id="main-title">SIMPLE BLOGGER</h1>
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
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
