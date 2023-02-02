<template>
  <div
      class="bookmark"
      @click="toggle"
  >
    <div class="bookmark__icon-container">
      <svg
          class="bookmark__icon"
          xmlns="http://www.w3.org/2000/svg"
          viewBox="0 0 50 50"
          width="50px"
          height="50px"
          :class="{'bookmark__icon--filled': isActive}"
      >
        <path
            fill="transparent"
            stroke="#757474"
            stroke-width="3px"
            d="M 37 48 C 36.824219 48 36.652344 47.953125 36.496094 47.863281 L 25 41.15625 L 13.503906 47.863281 C 13.195313 48.042969 12.8125 48.046875 12.503906 47.867188 C 12.191406 47.6875 12 47.359375 12 47 L 12 3 C 12 2.449219 12.449219 2 13 2 L 37 2 C 37.554688 2 38 2.449219 38 3 L 38 47 C 38 47.359375 37.808594 47.6875 37.496094 47.867188 C 37.34375 47.957031 37.171875 48 37 48 Z"
        />
      </svg>
    </div>
  </div>
</template>

<script setup>

import {ref} from "vue";

let isActive = ref(false)

function toggle() {
  isActive.value = !isActive.value
}
</script>

<style lang="scss" scoped>
.bookmark {
  cursor: pointer;

  &__icon-container {
    width: 30px;
    height: 30px;
    overflow: hidden;
    @media screen and (max-width: 800px) {
      width: 20px;
      height: 20px;
    }
  }

  &__icon {
    width: 100%;
    height: 100%;
    object-fit: contain;

    &--filled {
      & path {
        fill: #757474
      }
    }
  }
}
</style>
