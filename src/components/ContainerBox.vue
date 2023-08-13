<script setup></script>

<template>
    <div class="container">
        <slot></slot>
    </div>
</template>

<style lang="scss" scoped>
@import "../assets/styles/common.scss";

.container {
    max-width: 1100px;
    min-height: 100vh;
    margin: 0 auto;
    background-color: $background;
    background-image: url("../assets/image/background.jpg");
    background-size: cover;
    background-repeat: no-repeat;
    object-fit: cover;
}
</style>
