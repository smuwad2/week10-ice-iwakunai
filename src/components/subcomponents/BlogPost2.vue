<script>
    export default {
        // Add code if/as necessary
        // Hint: Add properties subject, entry and mood
        props: {
            subject: String,
            entry: String,
            mood: String,
            id: Number,
        },

    }
</script>


<template>
    <!-- TODO: add your template code here. Use boostrap card --> 
    <div class="card">
        <img class="card-img-top" v-bind:src="'/public/assets/'+ mood.toLowerCase() +'.png'"/>
        <div class="card-body">
            <h5 class="card-title">
                {{subject}}
            </h5>
            <p class="card-text">
                {{ entry }}
                <!-- <slot name="delete"></slot> -->
            </p>
        </div>
        <!-- <button  @click="deletePost(id)">
            Delete
            <slot name="delete"></slot>
        </button>             -->
        <slot name="delete"></slot>
        
    </div>
</template>

