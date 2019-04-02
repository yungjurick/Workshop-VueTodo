<template>
  <div class="mytodo">
    <div class="mytodo__container">
      <h1 class="mytodo__title">MY TODO LIST</h1>
      <section class="mytodo__container-top">
        <todoInput @addNewTodo="addTodo"/>
      </section>
      <section class="mytodo__container-bottom">
        <todoItems :propsData="todoItems" @deleteTodo="deleteTodo"/>
      </section>
    </div>
  </div>
</template>

<script>
import todoItems from "@/components/todoItems.vue";
import todoInput from "@/components/todoInput.vue";
export default {
  name: "app",
  components: {
    todoItems,
    todoInput
  },
  data() {
    return {
      newTodo: "",
      todoItems: [
        {
          id: 1,
          item: "CS Project"
        },
        {
          id: 2,
          item: "Algorithm Exam"
        },
        {
          id: 3,
          item: "IM Project"
        }
      ]
    };
  },
  methods: {
    addTodo(newTodo) {
      this.todoItems.push({
        id: this.todoItems.length + 1,
        item: newTodo
      });
    },
    deleteTodo(id) {
      this.todoItems = this.todoItems.filter(todo => todo.id != id);
    }
  }
};
</script>

<style>
body {
  font-family: Arial, Helvetica, sans-serif;
  margin: 0;
}
.mytodo {
  min-width: 100vw;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #3a4e7a;
}

.mytodo__container {
  min-height: 60vh;
  margin: 20vh 0;
  width: 50vw;
  box-shadow: 0 3px 6px rgba(0, 0, 0, 0.16), 0 3px 6px rgba(0, 0, 0, 0.23);
  background-color: #c2d2e9;
}

.mytodo__title {
  padding: 10px 0;
  margin: 0;
  text-align: center;
  background-color: #091d36;
  color: white;
}

.mytodo__container-top {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 64px;
}

.mytodo__container-bottom {
  display: flex;
  justify-content: center;
}
</style>
