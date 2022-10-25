<template>
    <h2>Task Tracker <Button title="Add Task" color="green" /></h2>

</template>

<script>
    import Button from "../components/Button";
    export default {
        name: "Header",
        components: {
            Button
        },
    }
</script>

<style scoped>
    h2{
        padding: 15px;
        border: 1px solid #2c3e50;
        text-align: left;
    }
</style>