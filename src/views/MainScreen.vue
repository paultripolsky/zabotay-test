<template>
  <Header/>
  <main class="main">
    <UIContainer>
      <TaskMain :task="task"/>
    </UIContainer>
  </main>
  <Footer/>
  <UITaskSwitcher/>
</template>

<script setup>
import UIContainer from '@/components/UI/UIContainer.vue'
import Header from '@/components/Header.vue'
import TaskMain from '@/components/Task/TaskMain.vue'
import UITaskSwitcher from '@/components/UI/UITaskSwitcher.vue'
import Footer from "@/components/Footer.vue";

let task = {
  taskNumber: 2,
  metaInformation: {
    source: 'Олимпиада Физтех',
    schoolClass: '11 класс',
    year: '2019 год',
  },
  taskSource: '../src/assets/images/svg/task-text.svg',
  taskImage: '../src/assets/images/svg/task-image.svg',
  answerItems: [
    {
      id: 1,
      requiredVariable: 'L',
      answer: 'Строка 1',
    },
    {
      id: 2,
      requiredVariable: 'I',
      answer: 2.5,
    },
  ],
  hints: {
    hint: '../src/assets/images/svg/hint.svg',
    solution: '../src/assets/images/svg/hint-complete.svg',
  },
}
</script>

<style lang="scss" scoped>
</style>
