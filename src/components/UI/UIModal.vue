<template>
  <div
      class="modal"
      v-if="show"
  >
    <div class="modal__wrapper">
      <div
          class="modal__content"
          ref="content"
      >
        <slot></slot>
      </div>
    </div>
  </div>
</template>

<script setup>
import useClickOutside from '@/composables/useClickOutside'
import {ref, watch} from 'vue'

let props = defineProps({
  show: {
    type: Boolean,
  },
})

let emit = defineEmits(['close'])


let content = ref(null)

useClickOutside(content, () => {
  emit('close', false)
})
</script>

<style lang="scss" scoped>
.modal {
  position: fixed;
  width: 100%;
  height: 100%;
  z-index: 100;
  top: 0;
  left: 0;
  background: rgba(0, 0, 0, 0.5);

  &__wrapper {
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  &__content {
    padding: 32px;
    background: $white;
    border-radius: 8px;
  }
}
</style>
