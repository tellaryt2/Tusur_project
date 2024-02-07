<script setup>
  import MainSidebarList from './MainSidebarList.vue';
</script>

<template>
    <div class="sidebar">
      <button class="sidebar__btn">
        <img src="/icons/array-back.svg" alt="">
        <p>Назад к списку курсов</p>
      </button>

      <MainSidebarList />

      <div class="sidebar__links">
        <div class="sidebar__link">
          <img src="/icons/participants.svg" alt="">
          <a href="">Участники</a>
        </div>
        <div class="sidebar__link">
          <img src="/icons/graphs.svg" alt="">
          <a href="">Оценки</a>
        </div>
      </div>
    </div>
</template>

<style>

.sidebar {
  z-index: 40;
  position: fixed;
  top: 75px; 
  left: 0;
  width: 335px;
  height: calc(100% - 75px); /* Высота экрана минус высота шапки */
  background-color: #FFF; 
  overflow: auto;

  border-top: solid 1px #A2ACBE;
}

.sidebar::-webkit-scrollbar {
    display: none;
}

.sidebar__btn {
  margin: auto;
  margin-top: 30px;
  margin-bottom: 20px;

  display: flex;
  column-gap: 20px;
  align-items: center;
  padding-left: 27px;
  padding-right: 27px;

  background-color: #FFF;

  border: solid 1px #A2ACBE;
  border-radius: 6px;
}

.sidebar__btn p{
  color: #2E3146;
  font-family: 'Montserrat', sans-serif;
  font-weight: 400;
  font-size: 15px;
  line-height: 1.2;
}

.sidebar__link {
  display: flex;
  margin-right: 30px;
  margin-left: 30px;
  margin-bottom: 20px;
  margin-top: 20px;
  column-gap: 20px;
}

.sidebar__link a{
  text-decoration: none;
  color: #2E3146;
}

@media (max-width: 1160px) {
  .sidebar {
    border-right: solid 1px #A2ACBE;
  }
}
</style>