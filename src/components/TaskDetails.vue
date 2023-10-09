<template>
    <div class="task">
        <h3>{{ task.title }}</h3>
        <div class="icons">
            <i class="material-symbols-outlined" @click="taskStore.deleteTask(task.id)">delete</i>
            <i class="material-symbols-outlined" :style="{ color: task.isFav ? '#ff005d' : '' }"
                @click="taskStore.toggleTask(task.id)">
                favorite
            </i>
        </div>
    </div>
</template>

<script setup>
import { useTaskStore } from '../store/TaskStore';

const taskStore = useTaskStore();

defineProps({
    task: {
        type: Object,
        required: true
    }
})

</script>