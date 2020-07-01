<template>
  <section class="todoapp">
    <header class="header">
      <h1>ToDos</h1>
      <input
        type="text"
        class="new-todo"
        placeholder="Ajouter une tâche..."
        v-model="newTodo"
        @keyup.enter="addTodo"
      />
    </header>

    <div class="main">
      <input type="checkbox" class="toggle-all" v-model="allDone"></input>
      <ul class="todo-list">
        <li class="todo" :class="{completed: todo.completed, editing: todo === editing }" v-for="todo in filteredTodos">
          <div class="view">
            <input type="checkbox" v-model="todo.completed" class="toggle" />
            <label @dblclick="zditTodo(todo)">{{ todo.name }}</label>
            <button class="destroy" @click.prevent="deleteTodo(todo)"></button>
          </div>
          <input type="text" class="edit" v-model="todo.name">
        </li>
      </ul>
    </div>

    <footer class="footer" v-show="todos.length > 0">
      <span class="todo-count">
        <strong>{{ remaining }}</strong> tâches à faire
      </span>
      <ul class="filters">
        <li>
          <a href="#" :class="{selected: filter === 'all'}" @click.prevent="filter = 'all'">Toutes</a>
        </li>
        <li>
          <a
            href="#"
            :class="{selected: filter === 'todo'}"
            @click.prevent="filter = 'todo'"
          >À faire</a>
        </li>
        <li>
          <a
            href="#"
            :class="{selected: filter === 'done'}"
            @click.prevent="filter = 'done'"
          >Terminées</a>
        </li>
      </ul>
      <button class="clear-completed" v-show="completed" @click.prevent="deleteCompleted">Supprimer</button>
    </footer>
  </section>
</template>

<script>
export default {
  data() {
    return {
      todos: [
        {
          name: "Tâche de test",
          completed: false
        }
      ],
      newTodo: "",
      filter: "all",
      editing: null
    };
  },
  methods: {
    addTodo() {
      this.todos.push({
        completed: false,
        name: this.newTodo
      });
      this.newTodo = "";
    },
    editTodo (todo) {
      this.editing = todo
    },
    deleteTodo(todo) {
      this.todos = this.todos.filter(i => i !== todo)
    },
    deleteCompleted () {
      this.todos = this.todos.filter(todo => !todo.completed)
    }

  },
  computed: {
    allDone: {
      get() {
        return this.remaining === 0;
      },
      set(value) {
        this.todos.forEach(todo => {
          todo.completed = value;
        });
      },
      hasTodos() {
        return this.todos.length > 0
      }
    },
    remaining() {
      return this.todos.filter(todo => !todo.completed).length;
    },
    completed () {
      return this.todos.filter(todo => todo.completed).length;
    },
    filteredTodos() {
      if (this.filter === "todo") {
        return this.todos.filter(todo => !todo.completed);
      } else if (this.filter === "done") {
        return this.todos.filter(todo => todo.completed);
      }
      return this.todos;
    }
  }
};
</script>

<style src="./Todos.css"></style>