<script>
    // Import BlogPost component

    import BlogPost2 from './subcomponents/BlogPost2.vue';
	import axios from 'axios'
    export default {
        data() {
            return {
                posts: [] // array of post objects
            }  
        },
        computed: {
            baseUrl() {
                // if (window.location.hostname=='localhost')
                //     return 'http://localhost:3000' 
                // else {
                //     const codespace_host = window.location.hostname.replace('5173', '3000')
                //     return `https://${codespace_host}`;
                // }
                return 'http://localhost:3000' 
            }
        },
        created() { // created is a hook that executes as soon as Vue instance is created
            axios.get(`${this.baseUrl}/posts`)
            .then(response => {
                // this gets the data, which is an array
                this.posts = response.data
                console.log(response.data)
            })
            .catch(error => {
                this.posts = [{ entry: 'There was an error: ' + error.message }]
            })
        },
        components: {
            BlogPost2,
        },
        methods: {
            async deletePost(id) {
                // TODO: Complete the delete method
                console.log(id)
                try{
                    const response = await axios.get(`${this.baseUrl}/deletePost`, {
                        params: {
                            id: id,
                        }
                    })
                    console.log(response.data)
                    this.posts = this.posts.filter(p => p.id !== id)
                }
                catch(error){
                    console.log(error)
                }
            }
        }
    }
</script>

<template>
   <!-- TODO: make use of the 'blog-post' component to display the blog posts -->
    <div v-for="post in posts" :key="post.id">
        <BlogPost2 :subject="post.subject" :entry="post.entry" :mood="post.mood">
            <template #delete>
                <button  @click="deletePost(post.id)">
                    Delete
                </button>           
            </template> 
        </BlogPost2>
    </div>

</template>


