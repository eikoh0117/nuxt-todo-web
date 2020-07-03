<template>
  <div v-if="user">
    <AddTodo @submit="addTodo" />
    <TodoList :todos="todos" />
  </div>
</template>

<script>
import AddTodo from "~/components/AddTodo.vue";
import TodoList from "~/components/TodoList.vue";
import axios from "~/plugins/axios";

export default {
  components: {
    AddTodo,
    TodoList
  },
  computed: {
    user() {
      return this.$store.state.currentUser;
    }
  },
  created() {},
  data() {
    return {
      todos: []
    };
  },
  methods: {
    async addTodo(todo) {
      const { data } = await axios.post("/v1/todos", { todo });
      // this.$store.commit("setUser", {
      //   ...this.user,
      //   todos: [...this.user.todos, data]
      // });
    }
  }
};
</script>
