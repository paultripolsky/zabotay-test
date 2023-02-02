<script setup>
import {RouterView} from 'vue-router'
</script>

<template>
  <div class="app__wrapper">
    <RouterView/>
  </div>
</template>

<style lang="scss" scoped>
.app {
  &__wrapper {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
    background: #10172a;
  }
}
</style>
