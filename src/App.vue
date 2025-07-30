<script setup lang="ts">
import { Notification } from 'fcm-rslib';

// const firebaseConfig = {
//   apiKey: 'AIzaSyANUdxcxppINSZkayH4nGn4t-lOTg3B7N4',
//   authDomain: 'my-landing-page-e7c7e.firebaseapp.com',
//   projectId: 'my-landing-page-e7c7e',
//   storageBucket: 'my-landing-page-e7c7e.firebasestorage.app',
//   messagingSenderId: '999813447171',
//   appId: '1:999813447171:web:4d47bb99b3fa66909a9836',
//   measurementId: 'G-43J14KHN0W',
// };

// const { requestPermissionAndGetToken, initializeFCM, listNotification } = useNotification();

// watch(listNotification, (newVal) => {
//   console.log('[APP] listNotification:', newVal);
// });

// onMounted(() => {
//   requestPermissionAndGetToken();
//   initializeFCM();
// });
</script>

<template>
  <div :style="{ display: 'flex', justifyContent: 'center', alignItems: 'center', height: '100vh' }">
    <Notification />
  </div>
</template>

<style scoped>
</style>
