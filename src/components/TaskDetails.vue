<template>
    <div class="task">
        <h3>{{ task.title }}</h3>
        <div class="icons">
            <i class="material-symbols-outlined">delete</i>
            <i class="material-symbols-outlined">favorite</i>
        </div>
    </div>
</template>

<script setup>

defineProps({
    task: {
        type: Object,
        required: true
    }
})

</script>