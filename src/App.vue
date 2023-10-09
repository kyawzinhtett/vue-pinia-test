<template>
  <header>
    <img src="./assets/pinia-logo.svg" alt="">
    <h1>Pinia Tasks</h1>
  </header>

  <main>
    <nav class="filter">
      <button @click="filter = 'all'">All tasks</button>
      <button @click="filter = 'favs'">Favorite tasks</button>
    </nav>

    <div class="task-list" v-if="filter === 'all'">
      <p>You have {{ taskStore.totalCount }} tasks left to do.</p>
      <div v-for="task in taskStore.tasks">
        <TaskDetails :task="task" />
      </div>
    </div>

    <div class="task-list" v-if="filter === 'favs'">
      <p>You have {{ taskStore.favCount }} favorite tasks left to do.</p>
      <div v-for="task in taskStore.favorites">
        <TaskDetails :task="task" />
      </div>
    </div>
  </main>
</template>

<script setup>
import { ref } from 'vue';
import { useTaskStore } from './store/TaskStore'
import TaskDetails from './components/TaskDetails.vue'

const taskStore = useTaskStore();
const filter = ref('all');

</script>