<script setup>
import { ref } from 'vue'
import AppCalendar from './components/AppCalendar.vue'

const selectedDate = ref(null)
const myInitialDate = '' // Если дата не указана, будет использоваться текущая дата
const locale = ref('ru')

const handleDateSelected = (date) => {
  selectedDate.value = date
}

const setLocale = (lang) => {
  locale.value = lang
}
</script>

<template>
  <main>
    <div class="locale-switcher">
      <button @click="setLocale('ru')" :class="{ active: locale === 'ru' }">Русский</button>
      <button @click="setLocale('enUS')" :class="{ active: locale === 'enUS' }">English</button>
    </div>

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
.locale-switcher {
  margin-bottom: 20px;
}
.locale-switcher button {
  margin: 0 5px;
  padding: 5px 10px;
  cursor: pointer;
  border: 1px solid #ccc;
  background-color: white;
  border-radius: 4px;
}
.locale-switcher button.active {
  background-color: #007bff;
  color: white;
  border-color: #007bff;
}
</style>