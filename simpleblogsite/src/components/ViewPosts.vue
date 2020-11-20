<template>
    <div class="view-posts-container">
        <h1 id="posts">Your Posts</h1>
        <h3 class="refresh-btn" @click="getPosts()">Refresh</h3>
        <div class="posts-container" v-for="post in posts" :key="post[3]">
            <div class="title-content">
                <h2><u>{{ post[2] }}</u></h2>
                <p class="date">Created On: {{ post[1] }}</p>
            </div>
            <br />
            <p>{{ post[0] }}</p>
            <delete-post :postId="post[3]"/>
            <edit-post :postId="post[3]"/>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import EditPost from "./EditPost.vue";
import DeletePost from "./DeletePost.vue";

    export default {
        name: 'ViewPosts',
        components: {
            EditPost,
            DeletePost
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
#posts {
    font-family: "Amatic SC", cursive;
    font-size: 42px;
    color: maroon;
}
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
    color: maroon;
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
    /* grid-template-columns: 2fr 2fr; */
    width: 50%;
    margin-left: 25%;
}
.date {
    font-size: 15px;
}
</style>