<template>
    <form @submit.prevent="saveTask()">
        <div>
            <label for="">Title: </label>
            <input type="text" name="title" v-model="title" id="">
        </div>
        <div>
            <label for="">User: </label>
            <input type="text" name="user" v-model="user" id="">
        </div>
        <div>
            <label for="">completed: </label>
            <input type="checkbox" name="completed" v-model="completed" id="">
        </div>

        <input type="submit" value="Save Task">
    </form>
</template>

<script>
    export default {
        name: "AddTask",
        props: {
          tasks: Object
        },
        data(){
            return{
                'title': '',
                'user': '',
                'completed': false,
            }
        },
        methods: {
            saveTask(){
                const newTask = {
                    id: Math.floor(Math.random() * 1000),
                    title: this.title,
                    user: this.user,
                    completed: this.completed,
                }

                this.$emit('add-task', newTask);

                this.title = ''
                this.user = ''
                this.completed = ''
            }
        }
    }
</script>

<style scoped>
    div{
        margin-bottom: 5px;
    }
    input{
        padding: 5px;
    }
</style>