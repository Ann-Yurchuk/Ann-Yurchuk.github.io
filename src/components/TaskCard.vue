<script setup>
import { SuccessFilled, EditPen, DeleteFilled } from "@element-plus/icons-vue";

const props = defineProps({
    todo: {
        type: Object,
        required: true,
    }
})

</script>

<template>
    <li class="todo">
        <input type="checkbox" :checked="todo.todo.isCompleted" />
        <div class="task">
            <input type="text" :value="todo.todo" />
        </div>
        <div class="task-actions">
            <el-icon :size="18" color="#28b043" class="icon">
                <SuccessFilled />
            </el-icon>
            <el-icon :size="18" color="#0f5bff" class="icon">
                <EditPen />
            </el-icon>
            <el-icon :size="18" class="icon">
                <DeleteFilled />
            </el-icon>
        </div>
    </li>
</template>


<style lang="scss" scoped>
@import '../assets/styles/common.scss';

.task {
    flex: 1;

    input {
        width: 100%;
        padding: 5px 10px;
        border: 1px solid $accent;
        border-radius: 10px;
        box-shadow: 0px 7px 16px -3px rgba(0, 0, 0, 0.5);
    }
}

.task-actions {
    display: flex;
    gap: 7px;
    /* opacity: 0; */
    transition: 150ms ease-in-out;
}
</style>