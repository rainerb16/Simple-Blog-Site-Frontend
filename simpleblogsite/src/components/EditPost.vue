<template>
    <div class="update-container">
        <h4 class="show-update-btn" v-on:click="isHidden = !isHidden">Click to Update</h4>
            <div v-if="!isHidden"> 
                <p>Blog Title</p>
                <input class="blog-title" type="text" v-model="blog_title" />
                <br />
                <p>Blog Content</p>
                <textarea type="text" v-model="blog_content" />
                <h4 class="update-btn" @click="updatePost()">Update Post</h4>
            </div>
    </div>
</template>

<script>
import axios from 'axios';

    export default {
        name: "EditPost",
        data() {
            return {
                blog_content: "",
                blog_title: "",
                isHidden: true
            }
        },
        props: {
            postId: {
                type: Number,
                required: true 
            },
        },
        methods: {
            updatePost: function() {
                axios.request({
                    url: "http://localhost:5000/blogs",
                    method: "PATCH",
                    headers: {
                        "Content-Type": "application/json"
                    },
                    data: {
                        content: this.blog_content,
                        id: this.postId
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
.update-container {
    width: 80%;
    margin-left: 10%;
    margin-top: 7vh;
}
textarea {
    width: 30vw;
    height: 10vh;
}
.update-btn {
    border: 1px solid black;
    width: 10%;
    margin-left: 45%;
    border-radius: 5%;
    margin-bottom: 5vh;
    margin-top: 3vh;
    cursor: pointer;
    color: maroon;
}
.show-update-btn {
    border: 1px solid black;
    width: 10%;
    margin-left: 45%;
    border-radius: 5%;
    cursor: pointer;
    color: maroon;
}
</style>