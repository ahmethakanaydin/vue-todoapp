<template>
  <div class="test">
    <input v-model="todo" type="text" class="form-control me-4" />
    <span class="addBtn">
      <button @click="handleSubmit" class="btn btn-primary mt-1">Ekle</button>
    </span>
  </div>
</template>

<script>
export default {
  data() {
    return {
      todo: "",
    };
  },
  methods: {
    handleSubmit() {
      if (this.todo === "") {
        alert("Alan boş eklenemez.");
      } else {
        this.$emit("new-item", this.todo);
        this.todo = "";
      }
    },
  },
};
</script>

<style scoped>
.test {
  display: flex;
  justify-content: center;
}

input {
  margin-top: 5px;
  border: none !important;
  border-radius: 100px !important;
  width: 75% !important;
  padding: 10px !important;
  /* float: left !important; */
  font-size: 16px !important;
}

button {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: auto;
  width: 150px;
  height: 45px;
  border-radius: 100px;
}
</style>
