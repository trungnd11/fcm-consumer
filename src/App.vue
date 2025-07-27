<script setup lang="ts">
import { useFcm } from 'fcm-client';
import { isRef, ref, watch, watchEffect } from 'vue';

const { requestPermissionAndGetToken, listenToForegroundMessages, listNotification } = useFcm();

requestPermissionAndGetToken();

listenToForegroundMessages();

watch(listNotification, () => {
  console.log({ listNotification });
  console.log('[APP] Vue ref:', ref);
  console.log('[APP] isRef', isRef(listNotification))
}, { immediate: true, deep: true })

watchEffect(() => {
  console.log('[APP] noti count:', listNotification.value.length);
});
</script>

<template>
  <div class="content">
    <h1>Rsbuild with Vue</h1>
    <p>Start building amazing things with Rsbuild.</p>
  </div>
</template>

<style scoped>
.content {
  display: flex;
  min-height: 100vh;
  line-height: 1.1;
  text-align: center;
  flex-direction: column;
  justify-content: center;
}

.content h1 {
  font-size: 3.6rem;
  font-weight: 700;
}

.content p {
  font-size: 1.2rem;
  font-weight: 400;
  opacity: 0.5;
}
</style>
