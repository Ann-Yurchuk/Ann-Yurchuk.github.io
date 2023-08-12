<script setup></script>

<template>
    <div class="container">
        <slot></slot>
    </div>
</template>


<style lang="scss" scoped>
@import '../assets/styles/common.scss';

.container {
    max-width: 1110px;
    min-height: 100vh;
    margin: 0 auto;
    background-color: $background;
}
</style>