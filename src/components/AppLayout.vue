<script setup>
import { ref } from "vue"
import { uid } from "uid";
import ContainerBox from './ContainerBox.vue'
import TaskInput from './TaskInput.vue'
import TaskCard from './TaskCard.vue'

const todoList = ref([])

const createTodo = (todo) => {
    todoList.value.push({
        id: uid(),
        todo,
        isCompleted: null,
        isEditing: null,
    })
};

const toggleTaskComplete = (todoPosition) => {
    todoList.value[todoPosition].isCompleted = !todoList.value[todoPosition].isCompleted
};

const toggleEditTask = (todoPosition) => {
    todoList.value[todoPosition].isEditing = !todoList.value[todoPosition].isEditing
};

const updateTask = (todoValue, todoPosition) => {
    todoList.value[todoPosition].todo = todoValue
};

const deleteTask = (todoId) => {
todoList.value = todoList.value.filter((todo)=> todo.id !== todoId)
}

</script>

<template>
    <div id="app">
        <ContainerBox>
            <div class="main">
                <h1>Create a task</h1>
                <TaskInput @create-todo="createTodo" />
                <div class="tasks" v-if="todoList.length > 0">
                    <h2 class="title">Select a task</h2>
                    <ul class="tasks-list">
                        <TaskCard v-for="(todo, index) in todoList" 
                        :todo="todo" 
                        :index="index"
                        @toggle-complete="toggleTaskComplete"
                        @edit-todo="toggleEditTask" 
                        @update-todo="updateTask"
                        @delete-todo="deleteTask" />
                    </ul>
                </div>
                <p v-else>There are no tasks to perform!..</p>
            </div>
        </ContainerBox>
    </div>
</template>

<style lang="scss" scoped>
@import '../assets/styles/common.scss';

#app {
    font-family: "Ubuntu", sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osk-font-smoothing: grayscale;
    text-align: center;
    color: $text;
    margin-bottom: 60px;
}

.tasks-list {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 20px;
    margin-top: 30px;
    margin-bottom: 30px;
}
</style>