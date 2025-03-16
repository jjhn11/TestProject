<script setup>
import Task from './Task.vue';
import { ref, defineProps, onMounted } from 'vue';
import axios from 'axios'

const props = defineProps({
    limit: Number
});

const tasks = ref([]);

onMounted(async () => {
    try {
        const response = await axios.get('http://localhost:8001/tasks');
        tasks.value = response.data.slice(0, props.limit);
    } catch (error) {
        console.error(error);
    }
});
</script>

<template>
    <div class="container mt-4">
        <h1 class="text-center mb-4">Tasks List</h1>
        <ul class="list-group">
            <Task v-for="task in tasks" :key="task.id" :task="task" />
        </ul>
    </div>
</template>

<style scoped>
.container {
    max-width: 600px;
    margin: auto;
}

h1 {
    font-size: 2.5rem;
    color: #343a40;
}

.list-group {
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    border-radius: 8px;
    overflow: hidden;
}
</style>