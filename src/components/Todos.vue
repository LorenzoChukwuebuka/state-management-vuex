<template>
  <main>
    <div>
      <div class="todos">
        <div class="todo" v-for="todo in allTodos" :key="todo.id">
          {{ todo.title }}
          <small>
            <i class="fa fa-trash" @click="deleteTodo(todo.id)"> </i>
          </small>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import { mapGetters, mapActions } from 'vuex'
export default {
  name: 'todo',

  computed: mapGetters(['allTodos']),
  created () {
    this.fetchTodos()
  },

  methods: {
    ...mapActions(['fetchTodos', 'deleteTodo'])
  }
}
</script>

<style scoped>
.todos {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 1rem;
}
.todo {
  border: 1px solid #ccc;
  background: #41b883;
  border-radius: 5px;
  text-align: center;
  position: relative;
  cursor: pointer;
}

small {
  position: absolute;
  bottom: 10px;
  right: 10px;
  color: white;
  cursor: pointer;
}
</style>
