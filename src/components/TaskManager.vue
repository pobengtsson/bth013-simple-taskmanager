<template>
  <div class="task-manager">
    <h1>Task Manager</h1>
    <input v-model="newTask" @keyup.enter="addTask" placeholder="Add a new task" />
    <ul>
      <li v-for="(task, index) in tasks" :key="index" v-bind:class="{ 'is-complete': task.completed }">
        {{ task.name }}
        <button @click="toggleComplete(index)">Toggle Complete</button>
        <button @click="deleteTask(index)">Delete</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: '',
      tasks: []
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim()) {
        this.tasks.push({ name: this.newTask, completed: false });
        this.newTask = '';
      }
    },
    toggleComplete(index) {
      this.tasks[index].completed = !this.tasks[index].completed;
    },
    deleteTask(index) {
      this.tasks.splice(index, 1);
    }
  }
};
</script>

<style scoped lang="scss">
.task-manager {
  width: 60vw;
  margin: 2rem;
  padding: 2rem;
  background-color: rgba(255, 255, 255, 0.85);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  border-radius: 8px;

  h1 {
    color: #4A90E2; /* A vibrant color that matches the background */
    text-align: center;
    margin-bottom: 1.5rem;
  }

  & input {
    width: 100%;
    padding: 0.5rem;
    margin-bottom: 1.5rem;
    border: 2px solid #4A90E2;
    border-radius: 4px;
    font-size: 1rem;
    &:focus {
      border-color: #7B61FF; /* A complementary vibrant color */
      outline: none;
    }
  }

  & ul {
    list-style-type: none;
    padding: 0;
  }

  & li {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 1rem;
    padding: 0.5rem;
    border-radius: 4px;
    background-color: rgba(255, 255, 255, 0.5); /* Slightly transparent */
    transition: background-color 0.3s ease;

    &:hover {
      background-color: rgba(255, 255, 255, 0.9);
    }

    &.is-complete {
      text-decoration: line-through;
      color: #6c757d;
    }
  }

  & button {
    padding: 0.25rem 0.5rem;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    background-color: #4A90E2;
    color: #fff;
    font-size: 0.875rem;
    transition: background-color 0.3s ease;

    &:hover {
      background-color: #7B61FF;
    }

    &:first-child {
      margin-right: 0.5rem;
    }
  }
}
</style>

