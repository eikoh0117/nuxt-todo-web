<template>
  <div>
    <AddTodo @submit="addTodo" />
    <TodoList :todos="todos" />
  </div>
</template>

<script>
import AddTodo from "~/components/AddTodo.vue";
import TodoList from "~/components/TodoList.vue";

export default {
  components: {
    AddTodo,
    TodoList
  },
  created() {
    console.log("API_KEY:", process.env.API_KEY);
  },
  data() {
    return {
      todos: []
    };
  },
  methods: {
    addTodo(title) {
      this.todos.push({
        title
      });
    }
  }
};
</script>
