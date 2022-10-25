<template>
    <button @click="clicked()" :style="{ background: color }" class="btn" > {{title}} </button>
</template>

<script>
    export default {
        name: "Button",
        props: {
            color: String,
            title: String
        },
        methods: {
            clicked() {
                console.log('Here');
            }
        }
    }
</script>

<style scoped>
    button{
        float: right;
        padding: 10px;
        size: 20px;
        font-weight: bold;
        color: aliceblue;
        border-radius: 3px;
    }
</style>