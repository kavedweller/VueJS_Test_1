<script setup>
import { ref } from 'vue'
</script>
<script>
import EditTask from './EditTask.vue';
const tasks = ref([{
  name: 'Task 1',
  time: 30
}, {
  name: 'Task 2',
  time: 40
}, {
  name: 'Task 3',
  time: 60
}, {
  name: 'Task 4',
  time: 45
}, {
  name: 'Task 5',
  time: 50
}]);
export default {
  components: {
    EditTask,
  },
  data() {
    return {
      tasks,
      showEditPopup: false,
      taskToEdit: null,
    };
  },
  methods: {
    openEditPopup(task) {
      this.taskToEdit = task;
      this.showEditPopup = true;
    },
    handleTaskUpdated() {
      this.showEditPopup = false;
      this.taskToEdit = null;
    },
  },
};
</script>

<template>
    <ul>
      <li v-for="task in tasks" :key="task.name">
        {{ task.name }} ({{ task.time }} minutes)
        <button @click="openEditPopup(task)">Edit</button>
      </li>
    </ul>

    <EditTask v-if="showEditPopup" @task-updated="handleTaskUpdated" :taskToEdit="taskToEdit" />
</template>

<style scoped>

</style>
