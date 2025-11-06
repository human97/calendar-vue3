<script setup>
import { ref } from 'vue'
import AppCalendar from './components/AppCalendar.vue'
import LocaleSwitcher from './components/LocaleSwitcher.vue'

const selectedDate = ref(null)
const myInitialDate = '' // Если дата не указана, будет использоваться текущая дата
const locale = ref('ru')

const handleDateSelected = (date) => {
  selectedDate.value = date
}
</script>

<template>
  <main>
    <LocaleSwitcher v-model="locale" />

    <AppCalendar
      :initial-date="myInitialDate"
      :locale="locale"
      @date-selected="handleDateSelected"
    />
    
    <div v-if="selectedDate" class="selected-date-info">
      Выбранная дата: {{ selectedDate.toLocaleDateString() }}
    </div>
  </main>
</template>

<style scoped>
main {
  padding: 20px;
  text-align: center;
}
.selected-date-info {
  margin-top: 20px;
  font-size: 1.2em;
}
</style>