<template>
    <div class="view-posts-container">
        <h1>Your Posts</h1>
        <h3 class="refresh-btn" @click="getPosts()">Refresh</h3>
        <div class="posts-container" v-for="post in posts" :key="post[3]">
            <div class="title-content">
                <h3><u>{{ post[2] }}</u> ---></h3>
                <p class="date">Created On: {{ post[1] }}</p>
            </div>
            <p>{{ post[0] }}</p>
            <edit-post :postId="post[3]"/>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import EditPost from "./EditPost.vue";

    export default {
        name: 'ViewPosts',
        components: {
            EditPost,
        },
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
.view-posts-container {
    margin-top: 10vh;
}
.refresh-btn {
    border: 1px solid black;
    width: 10%;
    margin-left: 45%;
    border-radius: 5%;
    margin-bottom: 5vh;
    margin-top: 3vh;
    cursor: pointer;
}
.posts-container {
    border: 1px solid black;
    margin-bottom: 1.5vh;
    width: 75%;
    margin-left: 12.5%;
}
.title-content {
    display: grid;
    align-items: center;
    justify-items: center;
    grid-template-columns: 2fr 2fr;
    width: 50%;
    margin-left: 25%;
}
.date {
    font-size: 15px;
}
</style>