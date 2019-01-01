<template>
  <div class="to-do-list">
    <h1>To Do List</h1>
    <form @submit.prevent="addToDo">
      <input type="text" v-model="todo" placeholder="To do..." />
    </form>
    <p>{{ todo }}</p>
    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        <input type="checkbox" id="done" v-model="todo.done" />
        {{ todo.item }}
        <i @click="removeToDo(index)">del</i>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'ToDoList',
  data() {
    return {
      todo: "",
      todos: [
        { item: "test", done: true },
        { item: "test2", done: false }
      ]
    }
  },
  methods: {
    addToDo() {
      this.todos.push({ item: this.todo, done: false });
      this.todo = '';
    },
    removeToDo(id) {
      this.todos.splice(id, 1);
    }
  }
}
</script>

<style scoped>
</style>
