<template>
  <div id="app">
    <AddTask @add-task="addTask" />
    <TaskList
      :tasks="tasks"
      @delete-task="deleteTask"
      @edit-task="editTask"
    />
  </div>
</template>

<script>
import AddTask from './components/AddTask.vue';
import TaskList from './components/TaskList.vue';

export default {
  components: {
    AddTask,
    TaskList
  },
  data() {
    return {
      tasks: [],
      nextTaskId: 1
    };
  },
  methods: {
    addTask(taskText) {
      this.tasks.push({ id: this.nextTaskId++, text: taskText });
    },
    deleteTask(taskId) {
      this.tasks = this.tasks.filter(task => task.id !== taskId);
    },
    editTask(updatedTask) {
      const taskIndex = this.tasks.findIndex(task => task.id === updatedTask.id);
      if (taskIndex !== -1) {
        this.tasks.splice(taskIndex, 1, updatedTask);
      }
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  background-image: url('https://i.pinimg.com/originals/43/af/d0/43afd01dc42127c352f1fde070cc2be0.jpg'); 
  background-size: cover; 
  background-position: center; 
  min-height: 100vh; 
  background-repeat: no-repeat;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
