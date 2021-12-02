<template>
  <div id="app">
    <div class="container">
      <filterTodo/>
      <addTodo />
      <h3>Todos</h3>
      <todo />
    </div>
  </div>
</template>

<script>
import todo from './components/Todos.vue'
import addTodo from './components/addTodo.vue'
import filterTodo from './components/filtertodos.vue'

export default {
  name: 'App',
  components: {
    todo,
    addTodo,
    filterTodo
  }
}
</script>

<style>
body {
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial,
    sans-serif;
  line-height: 1.6;
  background: #e8f7f0;
}
.container {
  max-width: 1100px;
  margin: auto;
  overflow: auto;
  padding: 0 2rem;
}
</style>
