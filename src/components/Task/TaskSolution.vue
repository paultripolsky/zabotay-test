<template>
  <div class="task-solution">
    <div class="task-solution__hint-links">
      <div
          @click="currentTab = 'hint'"
          class="task-solution__show-hint"
          :class="{ 'task-solution__show-hint--active': currentTab === 'hint' }"
      >
        Показать ответ
      </div>
      <div
          @click="currentTab = 'complete'"
          class="task-solution__show-hint"
          :class="{ 'task-solution__show-hint--active': currentTab === 'complete' }"
      >
        Показать решение
      </div>
    </div>
    <div
        v-if="currentTab === 'hint'"
        class="task-solution__hint"
    >
      <div class="task-solution__hint-container">
        <img
            class="task-solution__hint-img"
            :src="taskHint"
            alt=""
        />
      </div>
    </div>
    <div
        v-if="currentTab === 'complete'"
        class="task-solution__complete"
    >
      <div class="task-solution__hint-container">
        <img
            class="task-solution__hint-img"
            :src="taskSolution"
            alt=""
        />
      </div>
    </div>
  </div>
</template>

<script setup>
import {ref} from 'vue'

defineProps({
  taskHint: {
    type: String,
    required: true,
  },
  taskSolution: {
    type: String,
    required: true,
  },
})

let currentTab = ref(null)
</script>

<style lang="scss" scoped>
.task-solution {
  &__hint-links {
    display: flex;
  }

  &__show-hint {
    color: #53598e;
    cursor: pointer;
    text-decoration: underline;
    @media screen and (max-width: 800px) {
      font-size: 12px;
    }

    &--active {
      color: #7a82d3;
    }

    &:not(:first-child) {
      margin-left: 16px;
    }
  }

  &__hint-container {
    width: 400px;
    padding: 32px;
    border-radius: 8px;
    background: $white;
    margin-top: 32px;
    @media screen and (max-width: 800px) {
      width: 100%;
    }
  }

  &__hint-img {
    width: 100%;
    height: 100%;
    object-fit: contain;
  }
}
</style>
