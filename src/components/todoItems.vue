<template>
  <ul class="todoItems__container">
    <transition-group name="fade">
      <li v-for="todo in propsData" :key="todo.id" class="todoItem">
        <p class="todoItem__text">{{ todo.item }}</p>
        <button class="todoItem__button" @click="deleteItem(todo.id)">X</button>
      </li>
    </transition-group>
  </ul>
</template>

<script>
export default {
  name: "todoItems",
  props: ["propsData"],
  methods: {
    deleteItem(id) {
      this.$emit("deleteTodo", id);
    }
  }
};
</script>

<style>
.todoItem {
  color: #091d36;
  display: flex;
  justify-content: space-between;
  align-items: center;
  list-style-type: none;
  background-color: white;
  padding: 2% 10%;
}
.todoItem__text {
  margin: 0;
}
.todoItem__button {
  border-radius: 5px;
  border: 2px solid #091d36;
  font-size: 12px;
  font-weight: bold;
  background-color: white;
  color: #091d36;
  transition: all 0.2s;
  cursor: pointer;
}
.todoItem__button:hover {
  background-color: #091d36;
  color: white;
}
.todoItem + .todoItem {
  margin-top: 6px;
}
.todoItems__container {
  width: 100%;
  padding: 0 0 6px 0;
  margin: 0;
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
