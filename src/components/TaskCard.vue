<script setup>
import { SuccessFilled, EditPen, DeleteFilled } from "@element-plus/icons-vue";

const props = defineProps({
    todo: {
        type: Object,
        required: true,
    },
    index: {
        type: Number,
        required: true,
    },
});

defineEmits(["toggle-complete", "edit-todo", "update-todo", "delete-todo"]);
</script>

<template>
    <li class="todo">
        <input type="checkbox" 
        :checked="todo.isCompleted" 
        @input="$emit('toggle-complete', index)" />
        <div class="task">
            <input v-if="todo.isEditing" 
            type="text" 
            :value="todo.todo" 
            @input="$emit('update-todo', $event.target.value, index)"/>
            <span v-else>{{ todo.todo }}</span>
        </div>
        <div class="task-actions">
            <el-icon v-if="todo.isEditing" 
            :size="18" 
            color="#28b043" 
            class="icon" 
            @click="$emit('edit-todo', index)">
                <SuccessFilled />
            </el-icon>
            <el-icon v-else 
            :size="18" 
            color="#0f5bff" 
            class="icon" 
            @click="$emit('edit-todo', index)">
                <EditPen />
            </el-icon>
            <el-icon 
            :size="18" 
            class="icon" 
            @click="$emit('delete-todo', todo.id)">
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
}
</style>