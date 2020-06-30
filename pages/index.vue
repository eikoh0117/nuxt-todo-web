<template>
  <div>
    <AddTodo />
    <TodoList />
  </div>
</template>

<script>
import AddTodo from "~@components/AddTodo.vue";
import TodoList from "@/components/TodoList.vue";

export default {
  components: {
    AddTodo,
    TodoList
  },
  data() {
    return {
      todos: []
    };
  }
};
</script>
