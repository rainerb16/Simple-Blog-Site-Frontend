<template>
    <div>
        <h4 class="delete-btn" @click="deletePost()">Delete</h4>
    </div>
</template>

<script>
import axios from 'axios';

    export default {
        name: 'DeletePost',
        props: {
            postId: {
                type: Number,
                required: true
            },
        },
        methods: {
            deletePost: function() {
                axios.request({
                    url: "http://localhost:5000/blogs",
                    method: "DELETE",
                    headers: {
                        "Content-Type": "application/json"
                    },
                    data: {
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
.delete-btn {
    border: 1px solid black;
    width: 5%;
    margin-left: 47.5%;
    border-radius: 5%;
    margin-bottom: 5vh;
    margin-top: 3vh;
    cursor: pointer;
    color: maroon;
}
</style>