<template>
  <div class="container">
    <div class="header">
      <Title class="mb-4" :title="title" />
      <AddTodo @new-item="todoList.push({ title: $event })" />
    </div>

    <div class="text-center mt-3" v-if="todoList.length === 0">
      Henüz eklenmiş bir todo yok!
    </div>
    <TodoList :todoList="todoList" @delete-item="todoList = $event" />
  </div>
</template>

<script>
import Title from "@/components/Title";
import AddTodo from "@/components/AddTodo";
import TodoList from "@/components/TodoList";
export default {
  name: "App",
  components: {
    Title,
    AddTodo,
    TodoList,
  },
  data() {
    return {
      title: "My Todo List",

      todoList: [
        {
          title: "Vuejs Öğren",
          status: "done",
        },
        {
          title: "Laravel Öğren",
          status: "todo",
        },
      ],
    };
  },
};
</script>

<style>
.header {
  background-color: #f44336;
  padding: 30px 40px;
  color: white;
  text-align: center;
}
.header:after {
  content: "";
  display: table;
  clear: both;
}
</style>
