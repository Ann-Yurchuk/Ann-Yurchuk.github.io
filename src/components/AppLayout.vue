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
}

</script>

<template>
    <div id="app">
        <ContainerBox>
            <div class="main">
                <h1>Create TODO</h1>
                <TaskInput @create-todo="createTodo" />
                <div class="tasks">
                    <h2 class="title">Select a task</h2>
                    <ul class="tasks-list">
                        <TaskCard v-for="todo in todoList" :todo="todo"/>
                    </ul>
                </div>
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

.tasks-list{
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 20px;
    margin-top: 30px;
    margin-bottom: 30px;
}

</style>