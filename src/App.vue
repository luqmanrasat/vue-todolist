<template>
  <div id="app">
    <ToDoList></ToDoList>
  </div>
</template>

<script>
  import ToDoList from './components/ToDoList.vue'

  export default {
    name: 'app',
    components: {
      ToDoList
    }
  }
</script>

<style>
  @import url('https://use.fontawesome.com/releases/v5.6.3/css/all.css');

  ul {
    list-style-type: none;
    padding: 0;
  }
</style>
