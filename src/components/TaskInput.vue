<script setup>
import { reactive, defineEmits } from "vue";
import { toast } from "vue3-toastify";
import "vue3-toastify/dist/index.css";
import AddButton from "./AddButton.vue";

const emit = defineEmits(["create-todo"]);

const todoState = reactive({
  todo: "",
  invalid: null,
  errMessage: "",
});

const createTodo = () => {
  todoState.invalid = null;

  if (todoState.todo !== "") {
    emit("create-todo", todoState.todo);
    todoState.todo = "";
    return;
  }

  todoState.invalid = true;
  todoState.errMessage = toast.error(
    "Please enter the task text, it must not be empty!",
    {
      autoClose: 3000,
    }
  );
};
</script>

<template>
  <div class="wrapper">
    <el-input
      v-model="todoState.todo"
      class="input"
      placeholder="Please enter your task ..."
    />
    <AddButton @click="createTodo()" />
  </div>
</template>

<style lang="scss" scoped>
@import "../assets/styles/common.scss";
.wrapper {
  display: flex;
}
.input {
  width: 360px;
  font-size: 22px;
  border: 4px solid $accent;
  border-radius: 10px;
}
</style>
