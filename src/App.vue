<template>
  <main>
    <!-- heading -->
    <header>
      <img src="./assets/pinia-logo.svg" alt="">
      <h1>Pinia Tasks</h1>
    </header>

    <!-- new task form -->
    <div class="new-task-form">
      <TaskForm />
    </div>

    <!-- loading -->
    <div class="loading" v-if="loading">
      <p>Loading tasks...</p>
    </div>

    <!-- filter -->
    <nav class="filter">
      <button @click="filter = 'all'">All tasks</button>
      <button @click="filter = 'favs'">Favorite tasks</button>
    </nav>

    <div class="task-list" v-if="filter === 'all'">
      <p>You have {{ totalCount }} tasks left to do.</p>
      <div v-for="task in tasks">
        <TaskDetails :task="task" />
      </div>
    </div>

    <div class="task-list" v-if="filter === 'favs'">
      <p>You have {{ favCount }} favorite tasks left to do.</p>
      <div v-for="task in favorites">
        <TaskDetails :task="task" />
      </div>
    </div>

    <div class="reset-tasks">
      <button @click="taskStore.$reset">Reset</button>
    </div>
  </main>
</template>

<script setup>
import { ref } from 'vue';
import { storeToRefs } from 'pinia';
import { useTaskStore } from './store/TaskStore'
import TaskDetails from './components/TaskDetails.vue'
import TaskForm from './components/TaskForm.vue'

const taskStore = useTaskStore();
const { tasks, loading, favorites, favCount, totalCount } = storeToRefs(taskStore);
taskStore.getTasks();

const filter = ref('all');

</script>