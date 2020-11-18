<template>
    <div>
        <h1>Your Posts</h1>
        <h3 class="refresh-btn" @click="getPosts()">Refresh</h3>
        <div class="posts-container" v-for="post in posts" :key="post[3]">
            <h4>{{ post[2] }}</h4>
            <p>{{ post[0] }}</p>
        </div>
    </div>
</template>

<script>
import axios from 'axios';

    export default {
        name: 'ViewPosts',
        data() {
            return {
                posts: []
            }
        },
        methods: {
            getPosts: function() {
                axios.request({
                    url: "http://localhost:5000/blogs",
                    method: "GET"
                }).then((response) => {
                    console.log(response);
                    this.posts = response.data
                }).catch((error) => {
                    console.log(error);
                })
            }
        },
        mounted() {
            this.getPosts();
        }
    }
</script>

<style scoped>
.refresh-btn {
    border: 1px solid black;
    width: 10%;
    margin-left: 45%;
    border-radius: 5%;
    margin-bottom: 5vh;
    margin-top: 3vh;
    cursor: pointer;
}
</style>