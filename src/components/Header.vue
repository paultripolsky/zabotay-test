<template>
  <header class="header">
    <div class="header__wrapper">
      <UILogo class="header__logo"/>
      <div class="header__socials">
        <UISocialIcon
            class="header__social"
            v-slot="{ socialIconClass }"
        >
          <svg
              :class="socialIconClass"
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 48 48"
              width="48px"
              height="48px"
          >
            <path
                d="M5.83,23.616c12.568-5.529,28.832-12.27,31.077-13.203c5.889-2.442,7.696-1.974,6.795,3.434 c-0.647,3.887-2.514,16.756-4.002,24.766c-0.883,4.75-2.864,5.313-5.979,3.258c-1.498-0.989-9.059-5.989-10.7-7.163 c-1.498-1.07-3.564-2.357-0.973-4.892c0.922-0.903,6.966-6.674,11.675-11.166c0.617-0.59-0.158-1.559-0.87-1.086 c-6.347,4.209-15.147,10.051-16.267,10.812c-1.692,1.149-3.317,1.676-6.234,0.838c-2.204-0.633-4.357-1.388-5.195-1.676 C1.93,26.43,2.696,24.995,5.83,23.616z"
            />
          </svg>
        </UISocialIcon>
        <UISocialIcon
            class="header__social"
            v-slot="{ socialIconClass }"
        >
          <svg
              :class="socialIconClass"
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 48 48"
              width="48px"
              height="48px"
          >
            <path
                d="M45.763,35.202c-1.797-3.234-6.426-7.12-8.337-8.811c-0.523-0.463-0.579-1.264-0.103-1.776 c3.647-3.919,6.564-8.422,7.568-11.143C45.334,12.27,44.417,11,43.125,11l-3.753,0c-1.237,0-1.961,0.444-2.306,1.151 c-3.031,6.211-5.631,8.899-7.451,10.47c-1.019,0.88-2.608,0.151-2.608-1.188c0-2.58,0-5.915,0-8.28 c0-1.147-0.938-2.075-2.095-2.075L18.056,11c-0.863,0-1.356,0.977-0.838,1.662l1.132,1.625c0.426,0.563,0.656,1.248,0.656,1.951 L19,23.556c0,1.273-1.543,1.895-2.459,1.003c-3.099-3.018-5.788-9.181-6.756-12.128C9.505,11.578,8.706,11.002,7.8,11l-3.697-0.009 c-1.387,0-2.401,1.315-2.024,2.639c3.378,11.857,10.309,23.137,22.661,24.36c1.217,0.12,2.267-0.86,2.267-2.073l0-3.846 c0-1.103,0.865-2.051,1.977-2.079c0.039-0.001,0.078-0.001,0.117-0.001c3.267,0,6.926,4.755,8.206,6.979 c0.368,0.64,1.056,1.03,1.8,1.03l4.973,0C45.531,38,46.462,36.461,45.763,35.202z"
            />
          </svg>
        </UISocialIcon>
      </div>
      <div class="header__buttons">
        <UITextButton
            class="header__button text-button--empty"
            text="Зарегистрироваться"
        />
        <UITextButton
            class="header__button"
            text="Войти"
        />
      </div>
    </div>
  </header>
</template>

<script setup>
import UILogo from '@/components/UI/UILogo.vue'
import UITextButton from '@/components/UI/UITextButton.vue'
import UISocialIcon from '@/components/UI/UISocialIcon.vue'
</script>

<style lang="scss" scoped>
.header {
  height: 75px;
  background: $white;
  border-radius: 0 0 16px 16px;
  padding: 0 24px;

  &__wrapper {
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
  }

  &__logo {
    margin-bottom: 4px;
  }

  &__socials {
    display: flex;
    margin-left: auto;
    margin-right: 32px;
    @media screen and (max-width: 800px) {
      margin-right: 10px;
    }
    @media screen and (max-width: 600px) {
      display: none;
    }
  }

  &__social {
    &:not(:last-child) {
      margin-right: 8px;
    }
  }

  &__buttons {
    display: flex;
    @media screen and (max-width: 600px) {
      margin-left: auto;
    }
    @media screen and (max-width: 500px) {
      display: none;
    }
  }

  &__button {
    &:not(:last-child) {
      margin-right: 16px;
    }
  }
}
</style>
