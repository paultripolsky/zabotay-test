<template>
  <div class="task">
    <div class="task__wrapper">
      <div class="task__row">
        <div class="task__headline">Задача {{ task.taskNumber }}</div>
        <UIBookmark class="task__bookmark"/>
        <MetaInformation
            class="task__meta-information"
            :source="task.metaInformation.source"
            :school-class="task.metaInformation.schoolClass"
            :year="task.metaInformation.year"
        />
      </div>
      <div class="task__row">
        <TaskSource
            :src="task.taskSource"
            class="task__source"
        />
        <TaskImage
            :src="task.taskImage"
            class="task__image"
        />
      </div>
      <div class="task__row">
        <TaskAnswer :answerItems="task.answerItems"/>
      </div>
      <div class="task__row">
        <TaskSolution
            :taskHint="task.hints.hint"
            :taskSolution="task.hints.solution"
        />
      </div>
      <div class="task__row">
        <UIEmojiButton
            emoji="🤷‍"
            text="Не знаю, что делать :("
        />
      </div>
    </div>
  </div>
</template>

<script setup>
import MetaInformation from '@/components/MetaInformation.vue'
import UIBookmark from '@/components/UI/UIBookmark.vue'
import TaskImage from '@/components/Task/TaskImage.vue'
import TaskAnswer from '@/components/Task/TaskAnswer.vue'
import UIEmojiButton from '@/components/UI/UIEmojiButton.vue'
import TaskSource from '@/components/Task/TaskSource.vue'
import TaskSolution from '@/components/Task/TaskSolution.vue'

defineProps({
  task: {
    type: Object,
    required: true,
  },
})
</script>

<style lang="scss" scoped>
.task {
  padding: 40px 0;

  &__row {
    display: flex;
    width: 100%;

    &:nth-child(2) {
      margin-top: 50px;
      background: $white;
      padding: 24px 36px;
      border-radius: 8px;
      @media screen and (max-width: 1000px) {
        flex-direction: column;
      }
      @media screen and (max-width: 600px) {
        padding: 16px 10px;
      }
    }

    &:nth-child(3) {
      margin-top: 32px;
    }

    &:nth-child(4) {
      margin-top: 50px;
    }

    &:nth-child(5) {
      margin-top: 32px;
    }
  }

  &__headline {
    font-size: 30px;
    line-height: 125%;
    color: $white;
    margin-top: 16px;
    @media screen and (max-width: 800px) {
      font-size: 24px;
    }
    @media screen and (max-width: 360px) {
      font-size: 18px;
    }
  }

  &__meta-information {
    margin-left: auto;
  }

  &__bookmark {
    margin: 19px 0 0 10px;
  }

  &__source {
    width: 50%;
    @media screen and (max-width: 1000px) {
      width: 75%;
    }
    @media screen and (max-width: 800px) {
      width: 100%;
    }
  }

  &__image {
    width: 30%;
    margin-left: auto;
    @media screen and (max-width: 1000px) {
      width: 50%;
      margin-left: initial;
    }
    @media screen and (max-width: 800px) {
      width: 100%;
    }
  }
}
</style>
