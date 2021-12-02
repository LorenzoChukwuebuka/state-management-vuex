<template>
  <main>
    <div>
      <div class="legend">
        <span> Double click to mark as complete</span>
        <span> <span class="incomplete-box"></span> = Incomplete </span>
        <span> <span class="complete-box"></span> = Complete </span>
      </div>
      <div class="todos">
        <div
          @dblclick="onDblclick(todo)"
          class="todo"
          v-for="todo in allTodos"
          :key="todo.id"
          :class="{'is-complete':todo.completed}"
        >
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
    ...mapActions(['fetchTodos', 'deleteTodo', 'updateTodo']),
    onDblclick (todo) {
      const upTodo = {
        id: todo.id,
        title: todo.title,
        completed: !todo.completed
      }

      this.updateTodo(upTodo)
    }
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
  background: #48834d;
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
.legend {
  display: flex;
  justify-content: space-around;
  margin-bottom: 1rem;
}
.complete-box {
  display: inline-block;
  width: 10px;
  height: 10px;
  background: #35495e;
}
.incomplete-box {
  display: inline-block;
  width: 10px;
  height: 10px;
  background: #48834d;
}

.is-complete{
  background:#35495e;
  color:#fff;
}

@media (max-width: 500px) {
  .todos {
    grid-template-columns: 1fr;
  }
}
</style>
