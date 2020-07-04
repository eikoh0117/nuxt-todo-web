<template>
  <div v-if="user">
    <AddTodo @submit="addTodo" />
    <TodoList :todos="user.todos" />
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
      // ユーザー（とそれに紐づくTodo）を読み込み、TodoListを最新の状態に更新
      this.$store.commit("setUser", {
        ...this.user,
        todos: [...this.user.todos, data]
      });
    }
  }
};
</script>
