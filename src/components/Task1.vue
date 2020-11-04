<template>
  <div class="hello">
    <h2>{{ msg }}</h2>
    <p>
      For a guide and recipes on how to configure / customize this project,<br>
      check out the
      <a href="https://cli.vuejs.org" target="_blank" >vue-cli documentation</a>.
    </p>
    <h3>Task1: TODO List</h3>
    <div :style="{width: '70%', margin: 'auto'}">
      <ol>
        <li v-for="(todo, i) in todos" :key="i + todo.title">
          <div class="container">
            {{ todo.title }}
            <div>
              <input v-if="doEdit === i" @keyup.enter="editTodo(i)" v-model="editedTodoValue" type="text">
              <button @click="doEdit = i">EDIT</button>
              <button @click="removeTodo(i)">REMOVE</button>
            </div>
          </div>
        </li>
      </ol>
      <label> Add new Todo:
        <input @keyup.enter="addTodo" v-model="newTodoValue" type="text">
      </label>
      <button @click="addTodo">ADD todo</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Task1',
  props: {
    msg: String
  },

  data() {
    return {
      newTodoValue: "",
      editedTodoValue: "",
      doEdit: -1,
      todos: [
        {title: "Start"},
        {title: "Lorem ipsum dolor sit amet, consectetur adipisicing elit.  "},
        {title: "Consectetur adipisicing elit.  Molestias, veniam?"},
      ],

    }
  },

  methods: {
    addTodo() {
      if (this.newTodoValue.length !== 0) {
        this.todos.push({title: this.newTodoValue})
        this.newTodoValue = '';
      }
    },

    removeTodo(n) {
      // let i = this.todos.indexOf({'title': n});
      if (n !== -1) {
        this.todos.splice(n, 1)
      }
    },

    editTodo(n) {
      if (this.editedTodoValue.length > 0)
      this.todos[n].title = this.editedTodoValue
      this.editedTodoValue = '';
      this.doEdit = -1;
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h2, h3 {
  margin: 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  /*display: inline-block;*/
  margin: 0 10px;
  text-align: start;
  border: 1px solid lightgray;
}
a {
  color: #42b983;
}
.container {
  display: flex;
  justify-content: space-between;
}
</style>
