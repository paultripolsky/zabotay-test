<template>
  <div class="task-switcher">
    <div class="task-switcher__wrapper">
      <div
          class="task-switcher__trigger"
          @click.stop="contentVisible = !contentVisible"
          :class="{ 'task-switcher__trigger--green': contentVisible }"
          ref="trigger"
      >
        <img
            class="task-switcher__trigger-icon"
            src="@/assets/images/png/switcher.png"
            alt=""
        />
      </div>
      <div
          class="task-switcher__content"
          v-if="contentVisible"
          @click.stop
      >
        <div class="task-switcher__slider-headline">Выберите класс:</div>
        <div class="task-switcher__slide-prev classes-prev">←</div>

        <div class="task-switcher__slider">
          <div class="task-switcher__slide-prev classes-prev">←</div>
          <swiper
              :slides-per-view="3"
              :initial-slide="defaultActiveClassIndex"
              :modules="[Navigation]"
              :navigation="{
              clickable: true,
              nextEl: '.classes-next',
              prevEl: '.classes-prev',
            }"
              :centered-slides="true"
          >
            <swiper-slide
                class="task-switcher__slide"
                v-for="(item, index) of classes"
                :key="item"
                @click="defaultActiveClassIndex = index"
                :class="{ 'task-switcher__slide--active': index === defaultActiveClassIndex }"
            >
              {{ item }}
            </swiper-slide>
          </swiper>
          <div class="task-switcher__slide-next classes-next">→</div>
        </div>
        <div class="task-switcher__slider-headline">Выберите год:</div>
        <div class="task-switcher__slider">
          <div class="task-switcher__slide-prev years-prev">←</div>
          <swiper
              :slidesPerView="3"
              :initialSlide="defaultActiveYearIndex"
              :centeredSlides="true"
              :modules="[Navigation]"
              :navigation="{
              clickable: true,
              nextEl: '.years-next',
              prevEl: '.years-prev',
            }"
          >
            <swiper-slide
                class="task-switcher__slide"
                v-for="(item, index) of years"
                :key="item"
                @click="defaultActiveYearIndex = index"
                :class="{ 'task-switcher__slide--active': index === defaultActiveYearIndex }"
            >
              {{ item }}
            </swiper-slide>
          </swiper>
          <div class="task-switcher__slide-next years-next">→</div>
        </div>
        <div class="task-switcher__slider-headline">Выберите номер задачи:</div>
        <div class="task-switcher__slider">
          <div class="task-switcher__slide-prev issues-prev">←</div>
          <swiper
              :slides-per-view="5"
              :initial-slide="defaultActiveIssueNumberIndex"
              :centered-slides="true"
              :modules="[Navigation]"
              :navigation="{
              clickable: true,
              nextEl: '.issues-next',
              prevEl: '.issues-prev',
            }"
          >
            <swiper-slide
                class="task-switcher__slide"
                v-for="(item, index) of issueNumbers"
                :key="item"
                @click="defaultActiveIssueNumberIndex = index"
                :class="{ 'task-switcher__slide--active': index === defaultActiveIssueNumberIndex }"
            >
              {{ item }}
            </swiper-slide>
          </swiper>
          <div class="task-switcher__slide-next issues-next">→</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import {ref} from 'vue'
import {Swiper, SwiperSlide} from 'swiper/vue'
import 'swiper/css'
import 'swiper/css/navigation'
import {Navigation} from 'swiper'
import useClickOutside from '@/composables/useClickOutside'

let classes = ref([9, 10, 11])
let years = ref([2012, 2013, 2014, 2015])
let issueNumbers = ref([1, 2, 3, 4, 5, 6])

let defaultActiveClassIndex = ref(1)
let defaultActiveYearIndex = ref(3)
let defaultActiveIssueNumberIndex = ref(4)

let contentVisible = ref(false)

let trigger = ref(null)
useClickOutside(trigger, () => {
  contentVisible.value = false
})
</script>

<style lang="scss" scoped>
.task-switcher {
  z-index: 90;
  position: fixed;
  right: 32px;
  bottom: 32px;

  @media screen and (max-width: 400px) {
    right: 10px;
  }

  @media screen and (max-width: 300px) {
    right: 0;
  }

  &__wrapper {
    width: 100%;
    height: 100%;
  }

  &__trigger {
    width: 50px;
    height: 50px;
    padding: 12px;
    border-radius: 100%;
    cursor: pointer;
    background: #53598e;

    &--green {
      border: 1px solid #7edf7e;
    }

    &:hover {
      border: 1px solid #7edf7e;
    }
  }

  &__content {
    position: absolute;
    top: -320px;
    right: 0;
    display: flex;
    flex-direction: column;
    padding: 16px;
    background: $white;
    border-radius: 8px;
    @media screen and (max-width: 1000px) {
      top: -310px;
    }
  }

  &__trigger-icon {
    width: 100%;
    height: 100%;
    object-fit: contain;
  }

  &__slider-headline {
    font-size: 14px;
    line-height: 125%;
    text-align: center;

    &:not(:first-child) {
      margin-top: 10px;
    }
  }

  &__slider {
    padding: 8px 16px;
    background: #53598e;
    border-radius: 4px;
    display: flex;
    justify-content: center;
    margin-top: 4px;
    width: 250px;
    align-items: center;
  }

  &__slide {
    min-width: 50px;
    height: 35px;
    border-radius: 4px;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    color: $white;

    @media screen and (max-width: 400px) {
      min-width: initial;
      font-size: 12px;
    }

    &--active {
      background: #7a82d3;
    }

    &:hover {
      background: #7a82d3;
    }
  }

  &__slide-next,
  &__slide-prev {
    width: 20px;
    height: 20px;
    display: flex;
    align-items: center;
    justify-content: center;
    color: $white;
    cursor: pointer;
    padding: 0 4px;
  }
}
</style>
