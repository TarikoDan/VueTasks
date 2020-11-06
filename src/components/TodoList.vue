<template>
  <div>
<!--    Header-->
    <h2>{{ msg }}</h2>
    <p>
      For a guide and recipes on how to configure / customize this project,<br>
      check out the
      <a href="https://cli.vuejs.org" target="_blank" >vue-cli documentation</a>.
    </p>
    <h3>Task2: TODO List with Components</h3>

<!--    Finding-Component-->
    <FindTodo @findTodo="findTodo($event)">
      <template v-if="foundedTodoIndex >= 0" #number>
        {{ foundedTodoIndex + 1}}.
      </template>
      <TodoItem
          v-if="foundedTodoIndex >= 0"
          :todo="this.todos[foundedTodoIndex]"
          @removeTodo="removeTodo(foundedTodoIndex)"
      />
    </FindTodo>

<!--    #ALLTodos -List-->
    <div :style="{width: '70%', margin: 'auto'}">
      <ol>
        <li v-for="(todo, i) in todos" :key="i + todo.title">
          <TodoItem :todo="todo" @removeTodo="removeTodo(i)"
          />
        </li>
      </ol>

<!--      AddNew-Component-->
      <NewTodo @addTodo="addTodo"/>

    </div>
  </div>
</template>

<script>

import TodoItem from "@/components/TodoItem";
import NewTodo from "@/components/NewTodo";
import FindTodo from "@/components/FindTodo";

export default {
  name: 'TodoList',

  props: {
    msg: String
  },

  components: {
    TodoItem,
    NewTodo,
    FindTodo,
  },

  data() {
    return {
      todos: [
        {title: "Start"},
        {title: "Lorem ipsum dolor sit amet consectetur adipisicing elit"},
        {title: "Consectetur adipisicing elit"},
        {title: "For a guide and recipes on how to configure"},
        {title: "End"},
      ],
      foundedTodoIndex: -1
    }
  },

  methods: {
    addTodo(event) {
      this.todos.push({title: event})
    },

    removeTodo(n) {
      if (n !== -1) {
        this.todos.splice(n, 1)
        this.foundedTodoIndex = -1
      }
    },

    findTodo(ev) {
      let i = this.todos.findIndex((value) => value.title === ev);
      if (i >= 0) {
        this.foundedTodoIndex = i
      }else {
        this.foundedTodoIndex = -1
      }
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
