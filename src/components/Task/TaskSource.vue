<template>
  <div class="task-source">
    <img
        class="task-source__img"
        :src="src"
        alt=""
    />
  </div>
</template>

<script setup>
defineProps({
  src: {
    type: String,
    required: true,
  },
})
</script>

<style lang="scss" scoped>
.task-source {
  &__img {
    width: 100%;
    height: 100%;
    object-fit: contain;

    & path {
      fill: $black !important;
    }
  }
}
</style>
