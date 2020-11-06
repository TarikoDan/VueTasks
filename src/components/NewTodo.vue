<template>
  <div class="new">
    <label> Add new TODO:
      <input @keyup.enter="addTodo"
             v-model="newTodoValue"
             type="text"
             placeholder="Enter Title..."
      >
    </label>
    <button @click="addTodo">ADD TODO</button>
  </div>

</template>

<script>
export default {
  name: "NewTodo",

  data() {
    return {
      newTodoValue: "",
    }
  },

  methods: {
    addTodo() {
      if (this.newTodoValue.length !== 0) {
        this.$emit("addTodo", this.newTodoValue)
        this.newTodoValue = ""
      }
    },

  }
}
</script>

<style scoped>
* {
  color: #941616;

}
.new {
  border: 1px solid #b94242;
  width: 63%;
  margin: 10px auto;
  padding: 10px;
}

input, button {
  border: 2px inset #b94242;
}
button:hover {
  background-color: #ffc7c7;
}
</style>
