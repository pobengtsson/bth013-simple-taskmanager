<template>
    <TaskManager/>
</template>

<script>
import TaskManager from './components/TaskManager.vue'

export default {
  name: 'App',
  components: {
    TaskManager
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box; /* This ensures padding doesn't affect the overall dimensions of elements */
}

html, body {
  height: 100%; /* Make sure html and body are also taking full height */
  overflow: hidden; /* Hide overflow to prevent scroll */
}

#app {
  display: flex;
  justify-content: center;
  align-items: flex-start;
  height: 100vh; /* This makes sure that your app stretches to the full viewport height */
  background-image: url('./assets/task-manager-background.png');
  background-size: cover; /* This will cover the entire space available */
  background-position: center center;
  background-repeat: no-repeat;
}
</style>
