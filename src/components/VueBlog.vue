<template>
    <div>
        <ul>
            <Post 
            v-for="post in posts" 
            :key="post.title"
            :post="post"
            v-on:post-item-changed="Changed"
            />

        </ul>
    </div>
</template>

<script>
import Post from './BlogPosts.vue'
export default {
    props:['posts'],
    components: {Post},
    methods: {
        Changed(e){
            this.$emit('posts.changed',e)
        }
    },

    
}
</script>