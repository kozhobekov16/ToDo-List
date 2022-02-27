<template>
  <div class="bg-gray-900 text-white h-screen relative">
    <div class="main">
      <div class="second">
        <h1 class="text-center text-4xl font-semibold">ToDo App</h1>
        <div class="flex flex-col items-center">
          <input
            type="text"
            class="w-3/5 pl-2 p-2 mt-2 rounded text-gray-900 outline-none"
            v-model="current"
            v-on:keypress.enter="addTodo"
            placeholder="Type new todo"
          />
        </div>
        <div>
          <div class="length">
            <p v-if="todos.length">ToDo List</p>
            <p v-if="todos.length === 0">ToDo is Empty. Add a Todo list</p>
            <p>
              All ToDo Lists: <strong class="count">{{ todos.length }}</strong>
            </p>
          </div>
          <hr class="mt-2" />
          <ul v-for="(todo, i) in todos" :key="i">
            <li class="list">
              <p>{{ i + 1 }})</p>
              <p class="todo">{{ todo }}</p>
              <button @click="deleteTodo(i)" class="removeItem rounded">
                Remove
              </button>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "App",
  data() {
    return {
      todos: ["name"],
      current: "",
    };
  },
  methods: {
    inputH(e) {
      this.current = e.target.value;
    },
    addTodo() {
      localStorage.setItem("todoLists", this.todos.push(this.current));
      this.current = "";
    },
    deleteTodo(i) {
      this.todos.splice(i, 1);
    },
  },
};
</script>

<style src="../App.css">
</style>
