<template>
  <div
    class="row">
    <div
      class="col-lg-6">
      <h2>As minhas tarefas</h2>
    </div>
    <div
      class="col-lg-6">
      <button
        @click="deleteAll()"
        type="button"
        class="btn btn-outline-danger">
        Remover todas as tarefas
      </button>
    </div>
    <div
      class="col-lg-12 mt-4">
      <div
        v-if="!hasTodos"
        class="alert alert-success"
        role="alert">
        Não existem tarefas criadas!
      </div>

      <ul
        v-else
        class="list-group">
        <Todo
          v-for="(todo, index) in todos"
          :key="index"
          :todo="todo"
          :index="index"
          @delete-todo="deleteTodo"
          @mark-as-done="markAsDone"
          @unmark-as-done="unmarkAsDone"
          @change-todo="changeTodo"
        />
      </ul>
    </div>
    <div
      class="col-lg-12 mt-4">
      <div class="input-group mb-3">
        <input
          v-model="newTodo"
          @keyup.enter="addTodo()"
          type="text"
          class="form-control"
          placeholder="Insira aqui a sua tarefa ...">

        <button
          class="btn btn-outline-secondary"
          type="button"
          id="button-addon2"
          @click="addTodo()">
          Guardar
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import Todo from '@/components/Todo.vue'

export default {
  name: 'TodoList',

  components: {
    Todo
  },

  computed: {
    hasTodos () {
      return this.todos.length > 0
    }
  },

  data () {
    return {
      todos: [],

      newTodo: ''
    }
  },

  methods: {
    addTodo () {
      // Lógica do método

      if (this.newTodo === '') {
        this.$swal(
          'Erro',
          'Deverá preencher a descrição da tarefa!!',
          'error'
        )
        // alert('Deverá preencher a descrição da tarefa!!')

        return
      }

      const foundTodo = this.todos.find(todo => {
        return todo.description.trim().toLowerCase() === this.newTodo.trim().toLowerCase()
      })

      if (foundTodo) {
        this.$swal(
          'Erro',
          'Já existe uma tarefa com a mesma descrição!!',
          'error'
        )

        return
      }

      this.todos.push(
        {
          description: this.newTodo,
          done: false
        }
      )

      this.newTodo = ''

      this.$swal(
        'Sucesso',
        'Tarefa adicionada com sucesso!!',
        'success'
      )
    },

    markAsDone (todo) {
      todo.done = true
    },

    unmarkAsDone (todo) {
      todo.done = false
    },

    deleteTodo (index) {
      this.todos.splice(index, 1)
    },

    deleteAll () {
      this.todos = []
    }
  },

  created () {
  }
}
</script>

<style scoped>
  h3 {
    margin: 40px 0 0;
  }
  ul {
    list-style-type: none;
    padding: 0;
  }
  li {
    display: inline-block;
    margin: 0 10px;
  }
  a {
    color: #42b983;
  }

  .list-group-item {
    padding: 13px;
  }

  .margin-right {
    margin-right: 15px;
  }

  .todo-done {
    text-decoration: line-through;
  }
</style>
