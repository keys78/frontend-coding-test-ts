<template>
  <div
    v-for="notification in notifications"
    v-bind:key="notification.id"
    v-bind:class="notification.type"
    class="py-6 absolute top-10 right-10 px-6 rounded-md"
  >
    {{ notification.message }}
  </div>
</template>


<script setup lang="ts">
import { ref, watchEffect } from 'vue'
import useNotificationStore from '../store/notification'
import { Notification } from '../types/exercise'

const store = useNotificationStore()
const notifications = ref<Notification[]>(store.notifications)

watchEffect(() => {
  notifications.value = store.notifications
})
</script>

<style scoped>
.success {
  background: lightgreen;
}

.error {
  background: lightcoral;
}

.info {
  background: lightblue;
}
</style>
