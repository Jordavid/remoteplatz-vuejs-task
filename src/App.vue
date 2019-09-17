<template>
  <div id="app">
    <Task />
  </div>
</template>

<script>
import Task from './components/Task';
export default {
  name: 'app',
  components: {
    Task
  }
}
</script>

<style>
  .select-wrapper input.select-dropdown {
      border-bottom: none !important;
   }

   body {
     font-family: 'Raleway', sans-serif;
   }
</style>
