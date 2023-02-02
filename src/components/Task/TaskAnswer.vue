<template>
  <div class="task-answer">
    <div class="task-answer__row">
      <div class="task-answer__col">
        <div class="task-answer__headline">Введите ответ:</div>
        <div class="task-answer__items">
          <TaskAnswerItem
              @correct-answer-received="checkRightAnswers"
              class="task-answer__item"
              v-for="item in answerItems"
              :required-variable="item.requiredVariable"
              :answer="item.answer"
              @click.stop
          />
        </div>
      </div>
      <div class="task-answer__col">
        <UIArrowButton
            class="task-answer__button-further"
            :class="{ 'task-answer__button-further--green': allAnswersChecked }"
            :disabled="allAnswersChecked === false"
            text="Далее"
        />
      </div>
    </div>
    <UIModal
        :show="showModal"
        @close="showModal = false"
    >
      <div class="task-answer__modal">
        <div class="task-answer__modal-emoji">🥳</div>
        <div class="task-answer__modal-text">Поздравляю! Ты справился с задачей!</div>
        <UITextButton
            class="task-answer__modal-button"
            text="Далее"
        />
      </div>
    </UIModal>
  </div>
</template>

<script setup>
import {onBeforeMount, ref} from 'vue'

import TaskAnswerItem from '@/components/Task/TaskAnswerItem.vue'
import UIArrowButton from '@/components/UI/UIArrowButton.vue'
import UIModal from '@/components/UI/UIModal.vue'
import UITextButton from '@/components/UI/UITextButton.vue'

let props = defineProps({
  answerItems: {
    type: Array,
    required: true,
  },
})

let answers = []
let correctAnswersAmount = props.answerItems.length
let currentCorrectAnswersAmount = ref(0)
let showModal = ref(false)
let allAnswersChecked = ref(false)

onBeforeMount(() => {
  Array.from(props.answerItems).forEach((el) => {
    answers.push(el.answer.toString())
  })
})

function checkRightAnswers(value) {
  if (answers.includes(value.toString())) {
    currentCorrectAnswersAmount.value++
  }

  if (correctAnswersAmount === currentCorrectAnswersAmount.value) {
    showModal.value = true
    allAnswersChecked.value = true
  }
}
</script>

<style lang="scss" scoped>
.task-answer {
  width: 100%;

  &__row {
    display: flex;
    width: 100%;
    @media screen and (max-width: 800px) {
      flex-direction: column;
    }
  }

  &__col {
    display: flex;
    flex-direction: column;

    &:last-child {
      margin-left: auto;
      @media screen and (max-width: 800px) {
        margin-left: initial;
      }
    }
  }

  &__headline {
    font-size: 24px;
    line-height: 125%;
    color: $white;
    @media screen and (max-width: 800px) {
      font-size: 16px;
    }
  }

  &__items {
    display: flex;
    flex-direction: column;
    margin-top: 24px;
  }

  &__item {
    &:not(:first-child) {
      margin-top: 16px;
    }
  }

  &__button-further {
    margin: auto 0 0 auto;
    height: 50px;
    background: transparent;

    &:disabled {
      opacity: 0.5;
    }

    @media screen and (max-width: 800px) {
      margin-left: initial;
      width: fit-content;
      height: fit-content;
      margin-top: 24px;
    }

    &--green {
      border: 1px solid #7edf7e;
    }

    &:hover {
      border: 1px solid #7edf7e;
    }
  }

  &__modal {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }

  &__modal-emoji {
    font-size: 120px;
    @media screen and (max-width: 800px) {
      font-size: 80px;
    }
  }

  &__modal-button {
    margin-top: 25px;
  }

  &__modal-text {
    font-size: 24px;
    line-height: 125%;
    color: $black;
    @media screen and (max-width: 800px) {
      font-size: 18px;
    }
  }
}
</style>
