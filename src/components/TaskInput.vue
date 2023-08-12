<script setup>
import { ref } from "vue";
const input = ref("");
</script>

<template>
  <div>
    <el-input v-model="input" placeholder="Please enter your task ..." />
  </div>
</template>

<style lang="scss" scoped></style>
