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
    <input
      type="checkbox"
      :checked="todo.isCompleted"
      @input="$emit('toggle-complete', index)"
    />
    <div class="task">
      <input
        v-if="todo.isEditing"
        type="text"
        :value="todo.todo"
        @input="$emit('update-todo', $event.target.value, index)"
      />
      <span v-else>{{ todo.todo }}</span>
    </div>
    <div class="task-actions">
      <el-icon
        v-if="todo.isEditing"
        :size="24"
        color="#a3f341"
        class="icon"
        @click="$emit('edit-todo', index)"
      >
        <SuccessFilled />
      </el-icon>
      <el-icon
        v-else
        :size="24"
        color="#f3e741"
        class="icon"
        @click="$emit('edit-todo', index)"
      >
        <EditPen />
      </el-icon>
      <el-icon
        :size="24"
        color="#ea0e0e"
        class="icon"
        @click="$emit('delete-todo', todo.id)"
      >
        <DeleteFilled />
      </el-icon>
    </div>
  </li>
</template>

<style lang="scss" scoped>
@import "../assets/styles/common.scss";

.task {
  flex: 1;
  width: 240px;
  color: $textMuted;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  letter-spacing: 0.1em;

  input {
    width: 100%;
    font-size: 22px;
    padding: 5px 10px;
    border: none;
    outline: none;
    border-radius: 10px;
    box-shadow: 0px 7px 16px -3px rgba(0, 0, 0, 0.5);
  }
}

.task-actions {
  display: flex;
  gap: 7px;
}
</style>
