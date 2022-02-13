<template>
  <div class="container mx-auto max-w-screen-sm">
    <header class="text-center my-4">
      <h1 class="text-4xl font-bold">ToDo App</h1>
    </header>
    <div class="my-8">
      <form @submit.prevent="formSubmit">
        <input
          v-model="newToDo"
          type="text"
          placeholder="Add a task"
          class="w-full border border-2 border-teal-400 rounded px-4 py-4"
        />
      </form>
    </div>

    <div class="todo-cards">
      <div
        class="todo-card"
        v-for="todo in todos"
        :key="todo.id"
        :class="{ 'todo-card--done': todo.done }"
        @click="doneToggle(todo)"
      >
        <h3 class="todo-card__title">{{ todo.taskName }}</h3>
        <span>{{ todo.assignTime }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newToDo: "",
      todos: [],
    };
  },
  methods: {
    formSubmit() {
      const todo = {
        id: 2,
        taskName: this.newToDo,
        done: false,
        assignTime: Date(),
      };

      this.todos.unshift(todo);
      this.newToDo = '';
    },
    doneToggle(todo){
        return todo.done = !todo.done;
    }
  },
};
</script>