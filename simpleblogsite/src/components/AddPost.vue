<template>
    <div class="post-container">
        <h3>Add New Blog Post</h3>
        <p>Blog Title</p>
        <input class="blog-title" type="text" v-model="blog_title" />
        <br />
        <textarea type="text" v-model="blog_content" />
        <br />
        <p>Date</p>
        <input v-model="created_at" type="date" />
        <h4 class="post-btn" @click="addPost()">Post</h4>
    </div>
</template>

<script>
import axios from 'axios';

    export default {
        name: 'AddPost',
        data() {
            return {
                blog_content: "",
                created_at: "",
                blog_title: ""
            };
        },
        methods: {
            addPost: function() {
                axios.request({
                    url: "http://localhost:5000/blogs",
                    method: "POST",
                    headers: {
                        "Content-Type": "application/json"
                    },
                    data: {
                        content: this.blog_content,
                        created_at: this.created_at,
                        blog_title: this.blog_title
                    }
                }).then((response) => {
                    console.log(response)
                }).catch((error) => {
                    console.log(error)
                })
            }
        },
    }
</script>

<style scoped>
textarea {
    width: 30vw;
    height: 10vh;
}
.post-btn {
    border: 1px solid black;
    width: 10%;
    margin-left: 45%;
    border-radius: 5%;
    margin-bottom: 5vh;
    margin-top: 3vh;
    cursor: pointer;
}
.blog-title {
    margin-bottom: 2vh;
}
</style>