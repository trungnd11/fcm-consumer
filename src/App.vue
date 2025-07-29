<script setup lang="ts">
import { useFcm, Button, NotificationBell } from 'fcm-rslib';
import { isRef, watch, watchEffect } from 'vue';

const { requestPermissionAndGetToken, listenToForegroundMessages, listNotification } = useFcm();

console.log('[APP] listNotification:', listNotification);
console.log('[APP] isRef(listNotification):', isRef(listNotification));

requestPermissionAndGetToken();

listenToForegroundMessages();

watch(listNotification, (newVal, oldVal) => {
  console.log('[APP] listNotification changed:');
  console.log('  - Old:', oldVal);
  console.log('  - New:', newVal);
  console.log('  - Length:', newVal?.length);
}, { immediate: true, deep: true });

watchEffect(() => {
  console.log('[APP] watchEffect - noti count:', listNotification.value?.length);
});

// Test function to manually add notification
const addTestNotification = () => {
  const testNotification = {
    from: 'test-sender',
    messageId: `test-${Date.now()}`,
    notification: {
      title: 'Test Notification',
      body: 'This is a test notification'
    }
  };
  listNotification.value = [...(listNotification.value || []), testNotification];
  console.log('[APP] Added test notification:', testNotification);
};
</script>

<template>
  <div class="content">
    <h1>Rsbuild with Vue</h1>
    <p>Start building amazing things with Rsbuild.</p>
    <button @click="addTestNotification" class="test-button">
      Add Test Notification
    </button>
    <Button label="Click me" />
    <NotificationBell />
    <p>Notification count: {{ listNotification?.length || 0 }}</p>
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

.test-button {
  background: #007bff;
  color: white;
  border: none;
  padding: 0.5rem 1rem;
  border-radius: 4px;
  cursor: pointer;
  font-size: 1rem;
  margin: 1rem;
}

.test-button:hover {
  background: #0056b3;
}
</style>
