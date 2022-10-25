<template>
    <h2>Task Tracker
        <Button @toggle-add-task="$emit('showAddTask')" :title= "taskLabel ? 'Close' : 'Add Task'" :color="taskLabel ? 'red' : 'green'" />
    </h2>

</template>

<script>
    import Button from "../components/Button";
    export default {
        name: "Header",
        components: {
            Button
        },
        props: {
            taskLabel: Boolean,
            color: String
        }
    }
</script>

<style scoped>
    h2{
        padding: 15px;
        border: 1px solid #2c3e50;
        text-align: left;
    }
</style>