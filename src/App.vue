<template>
    <div class="container">
        <Header @showAddTask="showAddTask()" :taskLabel="showAddTaskForm" />
        <div v-show="showAddTaskForm">
            <AddTask @add-task="addTask" :tasks="tasks"/>
        </div>
        <Tasks @delete-task="deleteTask" @toggle-completed="toggleCompleted" :tasks="tasks"/>
    </div>
</template>

<script>

    import Header from "./components/Header";
    import Tasks from "@/components/Tasks";
    import AddTask from "@/components/AddTask";

    export default {
        name: 'App',
        components: {
            Header,
            AddTask,
            Tasks
        },
        data() {
            return {
                tasks: [],
                showAddTaskForm: false
            }
        },
        methods: {
            deleteTask(id) {
                if (confirm("Delete?")) {
                    this.tasks = this.tasks.filter((task) => task.id !== id);
                }
            },
            toggleCompleted(id) {
                this.tasks = this.tasks.map((task) => task.id === id ?
                    {...task, completed: !task.completed} : task
                )
            },
            addTask(newTask) {
                this.tasks = [...this.tasks, newTask]
            },
            showAddTask(){
                this.showAddTaskForm = !this.showAddTaskForm
            }
        },
        emits: ['delete-task', 'add-task'],
        created() {
            this.tasks = [
                {
                    id: 1,
                    title: "Have Lunch",
                    user: "john doe",
                    completed: true
                },
                {
                    id: 2,
                    title: "Have Breakfast",
                    user: "john doe",
                    completed: true
                },
                {
                    id: 3,
                    title: "Have Dinner",
                    user: "john doe",
                    completed: false
                },
            ]
        }
    }
</script>

<style>
    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
        border-color: 2px solid #2c3e50;
    }
</style>
