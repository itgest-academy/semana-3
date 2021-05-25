<template>
  <li
    class="list-group-item d-flex justify-content-between align-items-center">
    <span
      :class="{
        'todo-done': todo.done
      }">
      {{ index + 1 }} - {{ todo.description }}
    </span>

    <div>
      <button
        v-if="todo.done"
        @click="$emit('unmark-as-done', todo)"
        type="button"
        class="btn btn-outline-primary margin-right">
        Desmarcar como feita
      </button>

      <button
        v-if="!todo.done"
        @click="$emit('mark-as-done', todo)"
        type="button"
        class="btn btn-outline-success margin-right">
        Marcar como feita
      </button>

      <button
        @click="$emit('delete-todo', index)"
        type="button"
        class="btn btn-outline-danger">
        Apagar
      </button>
    </div>
  </li>
</template>

<script>
export default {
  name: 'Todo',

  props: {
    todo: {
      type: Object,
      required: true
    },

    index: {
      type: Number,
      required: true
    }
  },

  computed: {
  },

  data () {
    return {
    }
  },

  methods: {
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
