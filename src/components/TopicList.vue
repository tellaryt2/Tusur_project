<script setup>
import { ref, onMounted } from 'vue'

const showList = ref(false);

const isRotation = ref(false);

const textSecondListLibaryBtn = ref("Отметить как выполненный");

const textThirdListLibaryBtn = ref("Отметить как выполненный");

function toggleList() {
  showList.value = !showList.value;

  isRotation.value = !isRotation.value;
}

const props = defineProps({
    isMain: Boolean,
    textTitle: String,
    isFirstListLibary: Boolean,
    isGlossary: Boolean,
    isTask: Boolean,
    isSecondListLibary: Boolean,
    isSecondListLibaryAlert: Boolean,
    isSecondListLibaryFile: Boolean,
    isSecondListLibaryBtnActive: Boolean,
    isThirdListLibary: Boolean,
    isThirdListLibaryAlert: Boolean,
    isThirdListLibaryFile: Boolean,
    isThirdListLibaryBtnActive: Boolean
})

onMounted( () => {
    if (props.isSecondListLibaryBtnActive) textSecondListLibaryBtn.value = "✓ Выполнено";
    else textSecondListLibaryBtn.value = "Отметить как выполненный";

    if (props.isThirdListLibaryBtnActive) textThirdListLibaryBtn.value = "✓ Выполнено";
    else textThirdListLibaryBtn.value = "Отметить как выполненный";
})

</script>

<template>
  <div>
    <div class="topic" @click="toggleList">
        <div class="topic-title">
            <img src="/icons/arrow-inner.svg" alt="" :class="{ rotation: isRotation }">
            <p>{{textTitle}}</p>
        </div>
        <div v-if="isMain && showList" class="topic-title-close">
            <p>свернуть все</p>
        </div>
    </div>
    <ul v-if="showList" class="topic-lists">
      <p class="mateials">Материалы для изучения</p>
      <li v-if="isFirstListLibary" class="topic-list-li">
        <button class="topic-list">
            <div class="topic-list__info">
                <img src="/icons/libaryList.svg" alt="" />
                <p>Список литературы по модулю</p>
            </div>
            <div class="topic-list__mark">
                <div class="mark-progress">
                    <p>Надо сделать: <span>получить оценку</span></p>
                </div>
            </div>
        </button>
      </li>
      <li v-if="isGlossary" class="topic-list-li">
        <button class="topic-list">
            <div class="topic-list__info">
                <img src="/icons/glossary.svg" alt="" />
                <p>Глоссарий</p>
            </div>
            <div class="topic-list__mark">
                <div class="mark-btn no-active">
                    <p>Отметить как выполненный</p>
                </div>
            </div>
        </button>
      </li>
      <li v-if="isTask" class="topic-list-li">
        <button class="topic-list">
            <div class="topic-list__info">
                <img src="/icons/task-topic.svg" alt="" />
                <p>Задание</p>
            </div>
            <div class="topic-list__mark">
                <div class="mark-progress">
                    <p>Надо сделать: <span>получить оценку</span></p>
                </div>
                <div class="mark-complete">
                    <p>✓ Выполнено:<span>Посмотреть</span></p>
                </div>
                <div class="mark-complete">
                    <p>✓ Выполнено:<span>получить оценку</span></p>
                </div>
            </div>
        </button>
      </li>
      <li v-if="isSecondListLibary" class="topic-list-li">
        <button class="topic-list">
            <div class="topic-list__info">
                <img :src="isSecondListLibaryFile ? '/icons/file.svg' : '/icons/folder.svg'" alt="" />
                <p>Список литературы по модулю</p>
            </div>
            <div class="topic-list__mark">
                <div :class="{'mark-btn' : true,  'active': isSecondListLibaryBtnActive, 'no-active': !isSecondListLibaryBtnActive}">
                    <p>{{textSecondListLibaryBtn}}</p>
                </div>
            </div>
        </button>
        <div v-if="isSecondListLibaryAlert" class="topic-list__alert">
            <img src="/icons/lock.svg" alt="">
            <div>
                <p>Недоступно, пока не выполнено: Элемент курса</p>
                <p> <span>Задание</span> должен быть отмечен как выполненный</p>
            </div>
        </div>
      </li>
      <li v-if="isThirdListLibary" class="topic-list-li">
        <button class="topic-list">
            <div class="topic-list__info">
                <img :src="isThirdListLibaryFile ? '/icons/file.svg' : '/icons/folder.svg'" alt="" />
                <p>Список литературы по модулю</p>
            </div>
            <div class="topic-list__mark">
                <div :class="{'mark-btn' : true,  'active': isThirdListLibaryBtnActive, 'no-active': !isThirdListLibaryBtnActive}">
                    <p>{{textThirdListLibaryBtn}}</p>
                </div>
            </div>
        </button>
        <div v-if="isThirdListLibaryAlert" class="topic-list__alert">
            <img src="/icons/lock.svg" alt="">
            <div>
                <p>Недоступно, пока не выполнено: Элемент курса</p>
                <p> <span>Задание</span> должен быть отмечен как выполненный</p>
            </div>
        </div>
      </li>
    </ul>
  </div>
</template>

<style>
.topic {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 30px;
    cursor: pointer;
}

.topic-title {
    display: flex;
    column-gap: 14px;
    overflow: hidden;
    overflow-wrap: break-word;
    padding-left: 3px;
}

.topic-title p {
    color: #2E3146;
    font-size: 22px;
    font-weight: 500;
    line-height: 1.1;
    word-break: break-word;
}

.topic-title img {
    transition: transform 0.5s;
}

.rotation {
  transform: rotate(90deg);
}

.topic-title-close p {
    color: #273766;
    font-size: 16px;
    font-weight: 400;
    line-height: 1.4;
}

.mateials{
    color: #2E3146;
    font-size: 16px;
    font-weight: 400;
    line-height: 1.4;
}

.topic-lists {
    list-style-type: none;
    padding-left: 50px;
    padding-right: 30px;
    padding-bottom: 40px;
}

.topic-list-li {
    transition: background-color 0.3s;
    padding: 10px 20px 10px 20px;
}

.topic-list-li:hover {
    background-color: #E9F2FF66;
    border-radius: 5px;
}

.topic-list-li:hover > .topic-list__alert {
    background-color: #E9F2FF99;
}

.topic-list {
    display: flex;
    align-items: flex-start;
    justify-content: space-between;
    margin-bottom: 6px;

    width: 100%;
}

.topic-list__info {
    display: flex;
    column-gap: 20px;
}

.topic-list__info img {
    padding-top: 2px
}

.topic-list__info p {
    color: #2E3146;
    font-size: 16px;
    font-weight: 400;
    line-height: 1.4;
}

.topic-list__mark {
    margin-top: 13px;
    display: flex;
    flex-direction: column;
    row-gap: 6px;
    align-items: flex-end;
}

.topic-list__mark p{
    padding: 0px;
    margin: 0px;
}

.topic-list__alert {
    background-color: #E9EDF466;
    display: flex;
    column-gap: 15px;

    padding-left: 16px;
    border-radius: 5px;
}

.topic-list__alert div {
    padding-top: 8px;
    padding-bottom: 8px;
}

.topic-list__alert p {
    color: #2E3146;
    margin: 0px;

    font-size: 12px;
    font-weight: 400;
    line-height: 1.6;
}

.topic-list__alert span {
    font-weight: 500;
}

.mark-progress {
    background-color: #BCDFFF;
    border-radius: 15px;
    padding: 5px 12px 5px 12px;
}

.mark-progress p{
    color: #46495E;
    font-size: 12px;
    font-weight: 500;
    line-height: 1.25;
}


.mark-progress span {
    color: #46495E;
    font-size: 12px;
    font-weight: 400;
    line-height: 15px;
}

.mark-complete {
    background-color: #E7F3E9;
    border-radius: 15px;
    padding: 5px 12px 5px 12px;
}

.mark-complete p{
    color: #0E8321;
    font-size: 12px;
    font-weight: 500;
    line-height: 1.25;
}

.mark-complete span {
    color: #0E8321;
    font-size: 12px;
    font-weight: 400;
    line-height: 15px;
}

.mark-btn {
    border-radius: 5px;
    padding: 10px 15px 10px 15px;
}

.mark-btn p {
    font-size: 14px;
    font-weight: 400;
    line-height: 1.5;
}

.no-active {
    border: solid 1px #A2ACBE;
    transition: background-color 0.2s;
}

.no-active:hover {
    background-color: #f5f6f8;
}

.no-active p {
    color: #46495E;
}

.active {
    border: solid 1px #d7f7dc;
    transition: background-color 0.2s;
}

.active:hover {
    background-color: #f1f8f2;
}

.active p {
    color: #0E8345;
}


@media(max-width: 768px) {

    .topic-title p {
        font-size: 20px;
    }

    .topic-title-close p {
        font-size: 14px;
    }

    .mateials{
        font-size: 14px;
    }

    .topic-list__info {
        column-gap: 10px;
    }

    .topic-list__info p {
        max-width: 200px;
        font-size: 14px;
    }

    .mark-progress p{
        font-size: 10px;
    }

    .mark-progress span {
        font-size: 10px;
    }

    .mark-complete p{
        font-size: 10px;
    }

    .mark-complete span {
        font-size: 10px;
    }

    .mark-btn {
        padding: 10px 10px 10px 10px;
        text-align: center;
    }

    .mark-btn p {
        font-size: 10px;
    }
}

@media(max-width: 550px) {
    .topic {
        padding: 10px 30px;
    }

    .topic-list {
        flex-direction: column;
        align-items: stretch
    }

    .topic-list-li {
        padding: 10px 0px;
    }

    .topic-list__info {
        padding: 0px 5px;
    }

    .topic-list__mark {
        margin-top: 0px;
        padding-right: 30px;
    }

    .topic-list__alert {
        margin: 0px 30px 0px 0px;
    }

    .topic-list__alert p {
        font-size: 10px;
    }
}

</style>
