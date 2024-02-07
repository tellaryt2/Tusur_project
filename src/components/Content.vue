<script setup>
import { ref } from 'vue'

import Background from './Background.vue'
import DocenteList from './DocenteList.vue'
import ProgressBar from './ProgressBar.vue'
import TopicList from './TopicList.vue'

let isVariable = false

let titleText = ref('Финансовое управление и принципы планирования в здравоохранении')

const pText = `На курсе рассматриваются современные представления об 
    экономике здравоохранения и финансовом планировании, в том числе для ведения междисциплинарных проектов в сфере 
    медицины, экономики и инженерных технологий.`

let pTexts = ref([
  {
    id: 1,
    text: pText
  },
  {
    id: 2,
    text: pText
  }
])

const dataTopicList = ref([
  {
    id: 1,
    isMain: true,
    textTitle: 'Общее',
    isFirstListLibary: true,
    isGlossary: true,
    isTask: true,
    isSecondListLibary: true,
    isSecondListLibaryAlert: true,
    isSecondListLibaryFile: false,
    isSecondListLibaryBtnActive: false,
    isThirdListLibary: true,
    isThirdListLibaryAlert: false,
    isThirdListLibaryFile: true,
    isThirdListLibaryBtnActive: true
  },
  {
    id: 2,
    isMain: false,
    textTitle:
      'Модуль 1. Объекты интеллектуальной собственности. Интеллектуальные права. Правовая охрана объектов интеллектуальной собственности',
    isFirstListLibary: true,
    isGlossary: true,
    isTask: true,
    isSecondListLibary: true,
    isSecondListLibaryAlert: true,
    isSecondListLibaryFile: false,
    isSecondListLibaryBtnActive: false,
    isThirdListLibary: true,
    isThirdListLibaryAlert: false,
    isThirdListLibaryFile: true,
    isThirdListLibaryBtnActive: true
  },
  {
    id: 3,
    isMain: false,
    textTitle: 'Модуль 2. Объекты интеллектуальной собственности. Интеллектуальные права.',
    isFirstListLibary: true,
    isGlossary: false,
    isTask: false,
    isSecondListLibary: true,
    isSecondListLibaryAlert: false,
    isSecondListLibaryFile: true,
    isSecondListLibaryBtnActive: false,
    isThirdListLibary: true,
    isThirdListLibaryAlert: true,
    isThirdListLibaryFile: true,
    isThirdListLibaryBtnActive: false
  }
])

const addUpdate = () => {
  const newTopic = {
    id: 4,
    isMain: false,
    textTitle: `Модуль 4. Объекты интеллектуальной собственности. Интеллектуальные права. Правовая охрана объектов интеллектуальной собственности Модуль 4.
       Объекты интеллектуальной собственности. Интеллектуальные права. Правовая охрана объектов интеллектуальной собственности Модуль 4.
        Объекты интеллектуальной собственности. Интеллектуальные права. Правовая охрана объектов интеллектуальной собственности `,
    isFirstListLibary: true,
    isGlossary: true,
    isTask: true,
    isSecondListLibary: true,
    isSecondListLibaryAlert: true,
    isSecondListLibaryFile: false,
    isSecondListLibaryBtnActive: false,
    isThirdListLibary: true,
    isThirdListLibaryAlert: false,
    isThirdListLibaryFile: true,
    isThirdListLibaryBtnActive: true
  }

  const newPTexts = [
    {
      id: 3,
      text: pText
    },
    {
      id: 4,
      text: pText
    },
    {
      id: 5,
      text: pText
    }
  ]

  newPTexts.map((item) => pTexts.value.push(item))

  dataTopicList.value.push(newTopic)

  titleText.value = `Финансовое управление и принципы планирования в здравоохранении Финансовое управление и принципы планирования в здравоохранении`

  isVariable = true
}

const deleteUpdate = () => {
  dataTopicList.value = dataTopicList.value.filter((topic) => topic.id !== 4)

  pTexts.value = pTexts.value.filter((item) => item.id !== 3 && item.id !== 4 && item.id !== 5)

  titleText.value = `Финансовое управление и принципы планирования в здравоохранении`

  isVariable = false
}

window.addEventListener('keydown', (event) => {
  if (event.key === 'Enter' && !isVariable) addUpdate()
  else if (event.key === 'Enter' && isVariable) deleteUpdate()
})
</script>

<template>
  <div class="content">
    <div class="content-main">
      <div class="container">
        <div class="container__info">
          <div class="container__info-text">
            <h2>{{ titleText }}</h2>
            <img class="adaptive-img" src="/img/Img-container.png" alt="" />
            <p v-for="item in pTexts" :key="item.id">{{ item.text }} <br /></p>
          </div>
          <img class="fullhd-img" src="/img/Img-container.png" alt="" />
        </div>
        <DocenteList />
      </div>

      <div class="container">
        <ProgressBar />
      </div>

      <div class="container" v-for="item in dataTopicList" :key="item.id">
        <TopicList
          :isMain="item.isMain"
          :textTitle="item.textTitle"
          :isFirstListLibary="item.isFirstListLibary"
          :isGlossary="item.isGlossary"
          :isTask="item.isTask"
          :isSecondListLibary="item.isSecondListLibary"
          :isSecondListLibaryAlert="item.isSecondListLibaryAlert"
          :isSecondListLibaryFile="item.isSecondListLibaryFile"
          :isSecondListLibaryBtnActive="item.isSecondListLibaryBtnActive"
          :isThirdListLibary="item.isThirdListLibary"
          :isThirdListLibaryAlert="item.isThirdListLibaryAlert"
          :isThirdListLibaryFile="item.isThirdListLibaryFile"
          :isThirdListLibaryBtnActive="item.isThirdListLibaryBtnActive"
        />
      </div>
    </div>
    <Background />
  </div>
</template>

<style>
.content {
  margin-left: 335px;
  top: 75px;
}

.content-main {
  z-index: 10;
  top: 75px;
  position: relative;

  margin-top: 70px;
  padding-bottom: 90px;
}

.content::before {
  content: '';
  top: 242px;
  left: 335px;
  right: 0;
  bottom: 0;
  z-index: 5;
  background-color: #f5f5f5;
  position: fixed;
  border-radius: 20px 20px 0px 0px;
}

.container {
  max-width: 1100px;
  margin: auto;
  margin-bottom: 20px;
  border-radius: 10px;
  background-color: #ffffff;
}

.container__info {
  display: flex;
  column-gap: 40px;
  padding-left: 40px;
  padding-right: 40px;
  padding-top: 36px;
  padding-bottom: 36px;

  border-bottom: solid 1px #a2acbe;
}

.adaptive-img {
  display: none;
}

.container__info-text {
  overflow: hidden;
  word-wrap: break-word;
}

.container__info p {
  color: #2e3146;
  font-weight: 400;
  font-size: 14px;
  line-height: 1.4;
}

.container__info h2 {
  color: #2e3146;
  font-weight: 600;
  font-size: 28px;
  line-height: 1.2;
}

.fullhd-img {
  width: 210px;
  height: 200px;
  border-radius: 8px;
}

@media (max-width: 1450px) {
  .container {
    max-width: 800px;
  }
}

@media (max-width: 1160px) {
  .content {
    margin-left: 0px;
  }

  .content::before {
    left: 0px;
  }
}

@media (max-width: 768px) {
  .container {
    max-width: 550px;
  }

  .container__info {
    flex-direction: column;
  }

  .adaptive-img {
    margin-top: 15px;
    display: unset;

    width: 200px;
    height: 190px;
    border-radius: 8px;
  }

  .fullhd-img {
    display: none;
  }
}

@media (max-width: 550px) {
  .container {
    max-width: 355px;
  }

  .container__info p {
    font-size: 12px;
    line-height: 1.4;
  }

  .container__info h2 {
    font-size: 24px;
    line-height: 1.2;
  }

  .adaptive-img {
    width: 140px;
    height: 130px;
  }
}
</style>
