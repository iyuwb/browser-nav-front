<template>
    <div class="top-time">
        <h3>{{ formattedTime }}</h3>
    </div>
</template>
  
  <script setup>
import { ref, onMounted, onUnmounted } from "vue";

const formattedTime = ref("");

const updateTime = () => {
    const now = new Date();
    const hours = String(now.getHours()).padStart(2, "0");
    const minutes = String(now.getMinutes()).padStart(2, "0");
    formattedTime.value = `${hours}:${minutes}`;
};

onMounted(() => {
    updateTime();
    const timerId = setInterval(updateTime, 1000);

    onUnmounted(() => {
        clearInterval(timerId);
    });
});
</script>
  
  <style lang="less" scoped>
.top-time {
    margin: 2.5vh 0 2.5vh 0;
    text-align: center;
    h3 {
        display: inline-block;
        text-shadow: var(--timeShadow);
        font-size: 100px;
        font-weight: 700;
        letter-spacing: 0px;
        color: var(--timeColor);
    }
}
</style>