<script>
    export default {
        // Add code if/as necessary
        // Hint: Add properties subject, entry and mood
        props: {
            subject: String,
            entry: String,
            mood: String,
        }
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
            </p>
        </div>
    </div>
</template>

