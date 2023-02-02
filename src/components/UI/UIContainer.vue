<template>
  <div class="container">
    <slot></slot>
  </div>
</template>

<style lang="scss" scoped>
.container {
  width: 1200px;
  padding: 0 16px;
  margin: 0 auto;
  @media screen and (max-width: 1200px) {
    width: 992px;
  }
  @media screen and (max-width: 1000px) {
    width: 768px;
  }
  @media screen and (max-width: 800px) {
    width: 100%;
  }
}
</style>
