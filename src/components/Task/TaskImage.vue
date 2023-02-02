<template>
  <div class="task-image">
    <div class="task-image__container">
      <img
          class="task-image__source"
          :src="src"
          alt=""
      />
    </div>
    <UIZoom
        class="task-image__zoom"
        @click.stop="showModal = true"
    />
    <UIModal
        class="task-image__modal"
        :show="showModal"
        @close="closeModal"
    >
      <img
          class="task-image__modal-img"
          :src="src"
          alt=""
      />
    </UIModal>
  </div>
</template>

<script setup>
import {ref} from 'vue'
import UIZoom from '@/components/UI/UIZoom.vue'
import UIModal from '@/components/UI/UIModal.vue'

let showModal = ref(false)

defineProps({
  src: {
    type: String,
    required: true,
  },
})

function closeModal(val) {
  showModal.value = val
}
</script>

<style lang="scss" scoped>
.task-image {
  display: flex;
  flex-direction: column;

  &__container {
    padding: 16px;
  }

  &__source {
    width: 100%;
    height: 100%;
    object-fit: contain;
  }

  &__zoom {
    margin: 14px 12px 0 auto;
  }

  &__modal-img {
    width: 500px;
    padding: 0 32px;
    @media screen and (max-width: 600px) {
      width: 100%;
      height: auto;
    }
  }
}
</style>
