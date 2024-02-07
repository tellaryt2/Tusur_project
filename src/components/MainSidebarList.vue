<script setup>
import { ref } from 'vue'

import InsideSidebarList from './InsideSidebarList.vue'

const showList = ref(false);

const isRotation = ref(false);

let isVariable = false

function toggleList() {
  showList.value = !showList.value

  isRotation.value = !isRotation.value;
}

const dataItemSidebar = ref([
  {
    id: 1,
    text: 'Тема 1. Основы технологии производства ЭС'
  },
  {
    id: 2,
    text: 'Тема 2. Моделирование бизнес-процессов предметной области'
  },
  {
    id: 3,
    text: 'Тема 3. Модели разработки программного продукта'
  }
])

const addUpdate = () => {
  const newItemSidebar = {
    id: 4,
    text: 'Тема 4. Модели разработки программного продукта Модели разработки программного продукта Модели разработки программного продукта'
  }
  dataItemSidebar.value.push(newItemSidebar)
  isVariable = true
}

const deleteUpdate = () => {
  dataItemSidebar.value = dataItemSidebar.value.filter((item) => item.id !== 4)
  isVariable = false
}

window.addEventListener('keydown', (event) => {
  if (event.key === 'Enter' && !isVariable) addUpdate()
  else if (event.key === 'Enter' && isVariable) deleteUpdate()
})
</script>

<template>
  <div>
    <div class="main-list" @click="toggleList">
      <div class="main-list__info">
        <img src="/icons/list.svg" alt="" />
        <p>Содержание</p>
      </div>
      <div class="main-list__svg">
        <img src="/icons/arrow-list.svg" alt="" :class="{ rotation: isRotation }"/>
      </div>
    </div>
    <ul v-if="showList" class="main-list__lists">
      <li v-for="item in dataItemSidebar" :key="item.id">
        <InsideSidebarList :text="item.text" />
      </li>
    </ul>
  </div>
</template>

<style>
.main-list {
  display: flex;
  justify-content: space-between;
  margin-left: 30px;
  margin-right: 30px;
  align-items: center;
  cursor: pointer;
  background-color: #fff;
}

.main-list__info {
  display: flex;
  column-gap: 22px;
}

.main-list__info p {
  color: #2e3146;
  font-size: 14px;
  font-weight: 400;
  line-height: 1.5;
}

.main-list__lists {
  list-style-type: none;
  padding: 0;
  overflow: hidden;
}

.main-list__svg img {
  transition: transform 0.5s;
}

.rotation {
  transform: rotate(90deg);
}
</style>
