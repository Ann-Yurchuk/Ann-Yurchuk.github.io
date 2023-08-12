<script setup>
import ContainerBox from './ContainerBox.vue'
import TaskInput from './TaskInput.vue'
import AddButton from './AddButton.vue'
</script>

<template>
    <div id="app">
        <ContainerBox>
            <div class="main">
                <TaskInput />
                <AddButton />
                <div class="tasks">
                    <div class="title">Select a task</div>

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

.main {
    position: relative;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 30px;
    width: 100%;
    padding: 40px;
}
</style>