<script setup>
import { ref } from 'vue'
import AppCalendar from './components/AppCalendar.vue'

const selectedDate = ref(null)

const handleDateSelected = (date) => {
  selectedDate.value = date
}
</script>

<template>
  <main>
    <AppCalendar @date-selected="handleDateSelected" />
    <div v-if="selectedDate" class="selected-date-info">
      Выбранная дата: {{ selectedDate.toLocaleDateString() }}
    </div>
  </main>
</template>

<style>
#app {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-color: #f0f2f5;
}
main {
  padding: 20px;
  text-align: center;
}
.selected-date-info {
  margin-top: 20px;
  font-size: 1.2em;
}
</style>