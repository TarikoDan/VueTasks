<template>
  <div class="findBox">

    <label> Find TODO by Title:
      <input type="text" v-model="wantedTitle" @keyup.enter="findTodo" placeholder="Enter Title...">
    </label>
    <button @click="findTodo">FIND</button>

    <!-- Another Way to find by Index -->
<!--
    <label>
      <select v-model="selected">
        <option disabled value="">Choose indexTODO:</option>
        <option v-for="n in this.count" :key="n">{{ n }}</option>
      </select>
    </label>
    <span>{{ selected }}</span>
-->

    <div class="flex">
      <slot name="number" ></slot>
      <div class='findBox'>
        <slot>No such TODO</slot>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: "FindTodo",

  components: {
  },

  data() {
    return {
      wantedTitle: "",
    }
  },

  methods: {
    findTodo() {
      if (this.wantedTitle.length > 0) {
        this.$emit("findTodo", this.wantedTitle)
        this.wantedTitle = ""
      }
    }
  }
}
</script>

<style scoped>
* {
  color: #169461;
}
.findBox {
  border: 1px solid #42b983;
  width: 67%;
  margin: 10px auto;
  padding: 10px;
}

.flex {
  padding-left: 20px;
  display: flex;
  align-items: center;

}

input, button {
  border: 2px inset #42b983;
}
button:hover {
  background-color: #e1fff2;
}
</style>
