<script setup>
import { reactive, defineEmits } from "vue";
import { toast } from 'vue3-toastify';
import 'vue3-toastify/dist/index.css';
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
  todoState.errMessage = toast.error("Please enter text! Task value cannot be empty!", {
    autoClose: 3000,
  });

};

</script>

<template>
  <div class="wrapper" >
    <el-input v-model="todoState.todo" class="input" placeholder="Please enter your task ..." />
    <AddButton @click="createTodo()" />
  </div>
</template>

<style lang="scss" scoped>
.wrapper {
  display: flex;
}

</style>
