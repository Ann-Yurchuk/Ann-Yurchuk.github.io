<script setup>
import { Edit } from "@element-plus/icons-vue";
</script>

<template>
    <div>
        <el-button type="primary" :icon="Edit" round class="btn">Add task</el-button>
    </div>
</template>

<style lang="scss" scoped>
@import "../assets/styles/common.scss";

.btn {
    position: absolute;
    top: 115px;
    right: 27%;
    font-size: 18px;
    width: 150px;
    height: 45px;
    font-family: "Ubuntu", sans-serif;
    color: $text;
    background-color: $accent;
    border: none;
    box-shadow: 0px 3px 1px -2px rgba(0, 0, 0, 0.2),
        0px 2px 2px 0px rgba(0, 0, 0, 0.14), 0px 1px 5px 0px rgba(0, 0, 0, 0.12);

    &:hover,
    &:focus,
    &:active {
        background-color: darken($color: $accent, $amount: 30%);
        color: $textMuted;
    }
}
</style>
