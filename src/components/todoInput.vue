<template>
  <div class="todoInput__container">
    <input type="text" v-model="newTodo" class="todoInput__input">
    <button @click="addNewTodo" class="todoInput__button">SUBMIT</button>
  </div>
</template>

<script>
export default {
  name: "todoInput",
  data() {
    return {
      newTodo: ""
    };
  },
  methods: {
    addNewTodo() {
      this.$emit("addNewTodo", this.newTodo);
      this.newTodo = "";
    }
  }
};
</script>

<style>
.todoInput__container {
  width: 100%;
  display: flex;
  justify-content: center;
}
.todoInput__input {
  width: 50%;
  height: 24px;
  border: 0;
  margin-right: 12px;
}
.todoInput__button {
  height: 26px;
  font-weight: bold;
  color: white;
  border: 2px solid #3a4e7a;
  border-radius: 5px;
  background-color: #3a4e7a;
  cursor: pointer;
}

input:focus,
button:focus {
  outline: none;
}
</style>
