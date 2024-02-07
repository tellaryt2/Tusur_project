<script setup>
import { ref } from 'vue'

defineProps({
  text: String
})

const showList = ref(false);

const isRotation = ref(false);

function toggleList() {
  showList.value = !showList.value

  isRotation.value = !isRotation.value;
}
</script>

<template>
  <div class="inside-list">
    <div class="inside-list__content" @click="toggleList">
      <div class="inside-list__info">
        <p>{{text}}</p>
      </div>
      <div class="inside-list__svg">
        <img src="/icons/arrow-list.svg" alt="" :class="{ rotation: isRotation }"/>
      </div>
    </div>
    <ul v-if="showList" class="inside-list__lists">
      <li>
        <button class="inside-list__lists-btn">
          <div class="inside-list__lists-btn-info">
            <img src="/icons/task.svg" alt="" />
            <p>Задание</p>
          </div>
          <div class="inside-list__lists-btn-svg">
            <img src="/icons/ring.svg" alt="" />
          </div>
        </button>
      </li>
      <li>
        <button class="inside-list__lists-btn">
          <div class="inside-list__lists-btn-info">
            <img src="/icons/task.svg" alt="" />
            <p>Лекция</p>
          </div>
          <div class="inside-list__lists-btn-svg">
            <img src="/icons/ring.svg" alt="" />
          </div>
        </button>
      </li>
      <li>
        <button class="inside-list__lists-btn">
          <div class="inside-list__lists-btn-info">
            <img src="/icons/task.svg" alt="" />
            <p>Тест</p>
          </div>
          <div class="inside-list__lists-btn-svg">
            <img src="/icons/ring.svg" alt="" />
          </div>
        </button>
      </li>
      <li>
        <button class="inside-list__lists-btn">
          <div class="inside-list__lists-btn-info">
            <img src="/icons/task.svg" alt="" />
            <p>Форум</p>
          </div>
          <div class="inside-list__lists-btn-svg">
            <img src="/icons/ring.svg" alt="" />
          </div>
        </button>
      </li>
    </ul>
  </div>
</template>

<style>
.inside-list {
  background-color: #ecf1f880;
  border-radius: 8px;
  padding-bottom: 15px;

  transition: background-color 0.3s;
}

.inside-list:hover {
  background-color: #eef3fa;
}

.inside-list__content {
  display: flex;
  justify-content: space-between;
  margin-left: 74px;
  margin-right: 30px;
  align-items: center;
  cursor: pointer;
}

.inside-list__info {
  display: flex;
  column-gap: 22px;
}

.inside-list__info p {
  color: #2e3146;
  font-size: 14px;
  font-weight: 400;
  line-height: 1.5;
  word-break: break-word;
}

.inside-list__lists {
  list-style-type: none;
  margin-left: 74px;
  padding: 0;
  overflow: hidden;
}

.inside-list__svg img {
  transition: transform 0.5s;
}

.rotation {
  transform: rotate(90deg);
}

.inside-list__lists-btn {
  padding-left: 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: calc(100% - 50px);
  border: none;

  transition: background-color 0.3s;
}

.inside-list__lists-btn-info {
  display: flex;
  column-gap: 20px;
}

.inside-list__lists-btn-svg {
  padding-right: 10px;
}

.inside-list p {
  color: #2e3146;
  font-size: 14px;
  font-weight: 400;
  line-height: 1.5;
}

.inside-list__lists-btn:hover {
  cursor: pointer;
  background-color: #e0e8f4;
  border-radius: 6px;
}
</style>
