<template>
  <div class="task-answer-item">
    <div
        class="task-answer-item__key"
        :class="{ 'task-answer-item__key--green': isCorrectAnswer }"
    >
      {{ requiredVariable }}
    </div>
    <div class="task-answer-item__equally">=</div>
    <input
        type="text"
        class="task-answer-item__value"
        :class="{ 'task-answer-item__value--green': isCorrectAnswer }"
        v-model="inputValue"
        ref="input"
        :readonly="isCorrectAnswer"
    />
    <UITextButton
        :disabled="isCorrectAnswer"
        class="text-button--empty task-answer-item__button"
        :class="{ 'task-answer-item__button--no-drop': isCorrectAnswer }"
        text="Проверить"
        @click="checkAnswer"
    />
    <div
        v-if="isCorrectAnswer"
        class="task-answer-item__success-message"
    >
      Верно!
    </div>
    <div v-if="isCorrectAnswer === false" class="task-answer-item__error-message">
      Ответ неверный, подумай еще!
    </div>
  </div>
</template>

<script setup>
import UITextButton from '@/components/UI/UITextButton.vue'
import {ref} from 'vue'

let props = defineProps({
  requiredVariable: {
    type: String,
    required: true,
  },
  answer: {
    type: [String, Number],
    required: true,
  },
})

let emit = defineEmits(['correctAnswerReceived'])

let inputValue = ref('')
let isCorrectAnswer = ref(null)
let input = ref(null)

function checkAnswer() {
  if (inputValue.value.toString().toLocaleLowerCase().trim() === props.answer.toString().toLocaleLowerCase().trim()) {
    isCorrectAnswer.value = true
    emit("correctAnswerReceived", props.answer.toString())
  } else {
    isCorrectAnswer.value = false
    setTimeout(() => {
      isCorrectAnswer.value = null
    }, 3500)
  }
}
</script>

<style lang="scss" scoped>
.task-answer-item {
  display: flex;
  align-items: center;
  flex-wrap: wrap;

  &__key {
    color: $white;
    font-family: serif;
    font-size: 24px;
    line-height: 125%;
    width: 50px;
    height: 50px;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 8px;
    border: 1px solid $white;
    @media screen and (max-width: 800px) {
      width: 35px;
      height: 35px;
      font-size: 16px;
      flex-shrink: 0;
    }
    @media screen and (max-width: 400px) {
      font-size: 12px;
      width: 25px;
      height: 25px;
    }

    &--green {
      border: 1px solid #7edf7e;
      color: #7edf7e
    }
  }

  &__equally {
    color: $white;
    font-size: 24px;
    line-height: 125%;
    padding: 0 16px;
    @media screen and (max-width: 800px) {
      padding: 0 8px;
      font-size: 16px;
    }
  }

  &__value {
    height: 28px;
    padding: 0 16px;
    width: 300px;
    background: transparent;
    border-width: 0;
    border-bottom: 1px solid $white;
    appearance: none;
    color: $white;

    @media screen and (max-width: 800px) {
      width: 400px;
    }
    @media screen and (max-width: 620px) {
      width: 250px;
    }
    @media screen and (max-width: 460px) {
      width: 100px;
    }

    &--green {
      border-bottom: 1px solid #7edf7e;
      color: #7edf7e;
    }
  }

  &__button {
    margin-left: 16px;
    color: $white;

    &--no-drop {
      cursor: no-drop;
    }

    &:disabled {
      opacity: 0.5;
    }
  }

  &__success-message {
    color: #7edf7e;
    font-size: 14px;
    line-height: 125%;
    margin-left: 8px;
    @media screen and (max-width: 800px) {
      width: 100%;
      margin-top: 16px;
      font-size: 12px;
    }
  }

  &__error-message {
    color: #e64949;
    font-size: 14px;
    line-height: 125%;
    margin-left: 8px;
    @media screen and (max-width: 800px) {
      width: 100%;
      margin-top: 16px;
      font-size: 12px;
    }
  }
}
</style>
