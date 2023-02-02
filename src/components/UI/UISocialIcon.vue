<template>
  <div class="social-icon">
    <div class="social-icon__container">
      <slot :socialIconClass="socialIconClass"></slot>
    </div>
  </div>
</template>

<script setup>
let socialIconClass = 'social-icon__img'
</script>

<style lang="scss">
.social-icon {
  width: 40px;
  height: 40px;
  border-radius: 8px;
  overflow: hidden;
  border: 1px solid #464a68;
  padding: 7px;
  cursor: pointer;
  transition: all 0.2s ease-in-out;

  &__container {
    width: 100%;
    height: 100%;
  }

  &__img {
    width: 100%;
    height: 100%;
    object-fit: contain;
  }
}
</style>
