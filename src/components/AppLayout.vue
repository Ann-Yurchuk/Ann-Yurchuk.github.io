<script setup>
import { ref, watch, computed } from "vue";
import { uid } from "uid";
import ContainerBox from "./ContainerBox.vue";
import TaskInput from "./TaskInput.vue";
import TaskCard from "./TaskCard.vue";

const todoList = ref([]);

watch(
    todoList,
    () => {
        setTasksToLocalStorage();
    },
    {
        deep: true,
    }
);

const taskCompleted = computed(() => {
    return todoList.value.every((todo) => todo.isCompleted);
});

const fetchTodoList = () => {
    const saveTodoList = JSON.parse(localStorage.getItem("todoList"));
    if (saveTodoList) {
        todoList.value = saveTodoList;
    }
};

fetchTodoList();

const setTasksToLocalStorage = () => {
    localStorage.setItem("todoList", JSON.stringify(todoList.value));
};

const createTodo = (todo) => {
    todoList.value.push({
        id: uid(),
        todo,
        isCompleted: null,
        isEditing: null,
    });
};

const toggleTaskComplete = (todoPosition) => {
    todoList.value[todoPosition].isCompleted =
        !todoList.value[todoPosition].isCompleted;
};

const toggleEditTask = (todoPosition) => {
    todoList.value[todoPosition].isEditing =
        !todoList.value[todoPosition].isEditing;
};

const updateTask = (todoValue, todoPosition) => {
    todoList.value[todoPosition].todo = todoValue;
};

const deleteTask = (todoId) => {
    todoList.value = todoList.value.filter((todo) => todo.id !== todoId);
};
</script>

<template>
    <div id="app">
        <ContainerBox>
            <div class="main">
                <h1>Create a task</h1>
                <TaskInput @create-todo="createTodo" />
                <h2 class="title" v-if="todoList.length > 0">Select a task</h2>
                <div class="tasks" v-if="todoList.length > 0">
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
                <p v-else class="text">There are no tasks to perform!..</p>
                <transition name="bounce" 
                :duration="{ enter: 500, leave: 800 }">
                    <p v-if="taskCompleted && todoList.length > 0" class="text">
                        You have completed all your tasks!..
                    </p>
                </transition>
            </div>
        </ContainerBox>
    </div>
</template>

<style lang="scss" scoped>
@import "../assets/styles/common.scss";

.bounce-enter-active {
    animation: bounce-in 0.5s;
}

.bounce-leave-active {
    animation: bounce-in 0.5s reverse;
}

@keyframes bounce-in {
    0% {
        transform: scale(0);
    }

    50% {
        transform: scale(1.5);
    }

    100% {
        transform: scale(1);
    }
}
</style>
