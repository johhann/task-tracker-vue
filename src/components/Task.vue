<template>
    <div @dblclick="toggleCompleted(task.id)" :class="task.completed ?'completed':''">
        <h3>Title: {{task.title}}</h3>
        <h3>User: {{task.user}}</h3>
        <h3>completed: {{task.completed}}</h3>
        <button @click="removeTask(task.id)">Delete</button>
    </div>
</template>

<script>
    import Button from "@/components/Button";
    export default {
        name: "Task",
        components: {Button},
        props: {
            task: Object
        },
        methods:{
            removeTask(id){
                this.$emit('delete-task', id);
            },
            toggleCompleted(id){
                this.$emit('toggleCompleted', id);
            }
        }
    }
</script>

<style scoped>
    div{
        background-color: #c8cdd2;
        padding: 10px;
        margin-bottom: 15px;
    }
    button{
        padding: 8px;
        color: aliceblue;
        background-color: red;
        border-radius: 5px;
        border: none;
        cursor: pointer;
    }
    .completed{
        border-left: 10px solid green;
    }
</style>