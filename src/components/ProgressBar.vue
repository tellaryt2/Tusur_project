<script setup>
    const fillProcess = `${71}%`
</script>

<template>
    <div class="progress-content">
        <div class="progress-bar">
            <div class="progress" :style="{ width: fillProcess }"></div>
        </div>
        <p>{{ fillProcess }}</p>
    </div>
</template>

<style>

.progress-content {
    display: flex;
    column-gap: 30px;
    align-items: center;
    padding-right: 40px;
    padding-left: 40px;
}

.progress-content p{
    font-size: 24px;
    font-weight: 600;
    line-height: 1.25;
    letter-spacing: 0.03em;
}

.progress-bar {
  width: 100%;
  height: 10px;
  background-color: #A2ACBE33; 
  border-radius: 20px;
}

.progress {
  height: 100%;
  background-color: #3C388D; /* Цвет заполнения */
  border-radius: 20px;
}

@media(max-width: 550px) {
    .progress-content p{
        font-size: 22px;
    }
}
</style>