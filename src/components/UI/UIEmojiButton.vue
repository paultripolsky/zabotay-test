<template>
  <div class="emoji-button">
    <div class="emoji-button__icon">
      {{ emoji }}
    </div>
    <div class="emoji-button__text">
      {{ text }}
    </div>
  </div>
</template>

<script setup>
defineProps({
  emoji: {
    type: String,
    required: true,
  },
  text: {
    type: String,
    required: true,
  },
})
</script>

<style lang="scss" scoped>
.emoji-button {
  display: flex;
  align-items: center;
  padding: 8px 16px;
  border: 1px solid #464a68;
  border-radius: 8px;
  cursor: pointer;

  &:hover {
    border: 1px solid #e64949;
  }

  &__icon {
    margin-right: 16px;
    font-size: 24px;
    line-height: 125%;
  }

  &__text {
    font-size: 16px;
    line-height: 125%;
    color: $white;
  }
}
</style>
