<script setup>
import { reactive } from 'vue'
import { onMounted } from 'vue';
import axios from 'axios'

const form = reactive({
    // id: Number,
    taskTitle: '',
    // completed: false,
});

const handleSubmit = async () => {
    const newTask = { 
        id: Math.floor(Math.random() * 1000),
        titulo: form.taskTitle,
        completado: false   
     };
    try {
        const response = await axios.post('http://localhost:8001/tasks', newTask);
        form.taskTitle = '';
        
    } catch (error) {
        console.error(error);
    }
};
</script>

<template>
    <div class="container mt-4">
        <h1 class="text-center mb-4">Add Task</h1>
        <form @submit.prevent="handleSubmit">
            <div class="mb-3">
                <label for="taskTitle" class="form-label">Task Title</label>
                <input type="text" class="form-control" id="taskTitle" v-model="form.taskTitle" required>
            </div>
            <button type="submit" class="btn btn-primary">Add Task</button>
        </form>
    </div>
</template>