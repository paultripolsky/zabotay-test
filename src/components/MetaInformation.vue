<template>
  <div class="meta-information">
    <div class="meta-information__wrapper">
      <p class="meta-information__text">
        {{ source }}
        <br/>
        {{ schoolClass }}, {{ year }}
      </p>
    </div>
  </div>
</template>

<script setup>
defineProps({
  source: {
    type: String,
    required: true,
  },
  schoolClass: {
    type: String,
    required: true,
  },
  year: {
    type: String,
    required: true,
  },
})
</script>

<style lang="scss" scoped>
.meta-information {
  padding: 12px 16px;
  border-radius: 8px;
  border: 1px solid #555a88;
  display: flex;
  width: fit-content;

  &__text {
    font-size: 16px;
    line-height: 125%;
    color: #e8e8e8;
    font-weight: 300;
    @media screen and (max-width: 800px) {
      font-size: 14px;
    }
    @media screen and (max-width: 360px) {
      font-size: 12px;
    }
  }
}
</style>
