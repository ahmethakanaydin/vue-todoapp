<template>
  <ul>
    <li v-for="todo in todoList" :key="todo">
      {{ todo.title }}

      <span @click="deleteItem(todo)"
        ><i class="far fa-trash-alt float-end text-danger me-3"></i>
      </span>
    </li>
  </ul>
</template>

<script>
export default {
  props: ["todoList"],
  data() {
    return {
      todoLocal: this.todoList,
    };
  },
  methods: {
    deleteItem(todo) {
      this.todoLocal = this.todoLocal.filter((t) => t != todo);
      this.$emit("delete-item", this.todoLocal);
    },
  },
};
</script>

<style scoped>
ul {
  margin: 0;
  padding: 0;
}
ul li {
  cursor: pointer;
  position: relative;
  padding: 12px 8px 12px 40px;
  background: #eee;
  font-size: 18px;
  transition: 0.2s;
  list-style-type: none;

  /* make the list items unselectable */
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

li.done {
  text-decoration: line-through;
}

ul li:nth-child(odd) {
  background: #f9f9f9;
}

ul li:hover {
  background: #ddd;
}
</style>
