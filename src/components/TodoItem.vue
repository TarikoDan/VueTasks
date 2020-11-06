<template>
  <div class="container">
    {{ todo.title }}
    <div>
      <input v-if="doEdit" @keyup.enter="editTodo" v-model="editedTodoValue" type="text">
      <button @click="doEdit = !doEdit">EDIT</button>
      <button @click="destroy">REMOVE</button>
    </div>
  </div>

</template>

<script>
export default {
  name: "TodoItem",

  props: {
    todo: Object,
  },

  data() {
    return {
      doEdit: false,
      editedTodoValue: this.todo.title,
    }
  },

  methods: {
    editTodo() {
      if (this.editedTodoValue.length > 0) {
        this.todo.title = this.editedTodoValue
        this.editedTodoValue = ""
      }
      this.doEdit = false
    },

    destroy(){
      this.$emit("removeTodo")
    },
  },

}
</script>

<style scoped>

</style>
