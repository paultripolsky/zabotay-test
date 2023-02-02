<template>
  <button class="text-button">
    {{ text }}
  </button>
</template>

<script setup>
defineProps({
  text: {
    type: String,
    required: true,
  },
})
</script>

<style lang="scss" scoped>
.text-button {
  padding: 8px 16px;
  border-radius: 8px;
  border: 1px solid #464a68;
  background: #464a68;
  font-size: 16px;
  line-height: 125%;
  cursor: pointer;
  transition: all 0.2s ease-in-out;
  color: $white;
  display: flex;
  align-items: center;
  justify-content: center;
  @media screen and (max-width: 800px) {
    font-size: 12px;
  }
  @media screen and (max-width: 400px) {
    padding: 4px 8px;
  }

  &:hover {
    background: #383b53;
  }

  &--empty {
    border: 1px solid #464a68;
    background: transparent;
    color: $black;

    &:hover {
      background: #464a68;
      color: $white;
    }
  }
}
</style>
