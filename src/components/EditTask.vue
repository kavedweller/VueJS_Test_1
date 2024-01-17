<template>
    <div v-if="taskToEdit">
        <form @submit.prevent="updateTask">
            <input type="text" v-model="editedTaskName" placeholder="Task Name">
            <input type="number" v-model="editedTaskTime" placeholder="Time (minutes)">
            <button type="submit">Update Task</button>
        </form>
    </div>
</template>

<script>
export default {
    emits: ['task-updated'],
    props: {
        taskToEdit: Object,
    },
    data() {
        return {
            editedTaskName: this.taskToEdit.name,
            editedTaskTime: this.taskToEdit.time,
        };
    },
    methods: {
        updateTask() {
            this.$emit('task-updated');
        },
    },
};
</script>