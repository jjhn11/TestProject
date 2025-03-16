<script setup>
import { defineProps } from 'vue';

const props = defineProps({
    task: {
        type: Object,
        required: true,
        default: () => ({
            id: 0,
            titulo: '',
            completado: false
        })
    }
});
</script>

<template>
    <li class="list-group-item d-flex justify-content-between align-items-center task-item">
        <span :class="{ 'text-decoration-line-through': task.completado }">{{ task.titulo }}</span>
        <span class="badge rounded-pill" :class="task.completado ? 'bg-success' : 'bg-warning'">
            {{ task.completado ? 'Completed' : 'Pending' }}
        </span>
    </li>
</template>

<style scoped>
.task-item {
    transition: background-color 0.3s ease;
}

.task-item:hover {
    background-color: #f8f9fa;
}

.text-decoration-line-through {
    text-decoration: line-through;
}
</style>