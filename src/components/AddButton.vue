<script setup>
import { Edit } from "@element-plus/icons-vue";
</script>

<template>
    <div>
        <el-button type="primary" :icon="Edit" round class="btn">Add task</el-button>
    </div>
</template>
  
<style lang="scss" scoped>
@import '../assets/styles/common.scss';

.btn {
    position: absolute;
    top: 50;
    right: 25%;
    font-size: 16px;
    font-family: "Ubuntu", sans-serif;
    background-color: $accent;
    border-color: $accent;
    color: $backgroundMuted;

    &:hover,
    &:focus,
    &:active {
        background-color: darken($color: $accent, $amount: 10%);
        border-color: darken($color: $accent, $amount: 10%);
    }
}
</style>