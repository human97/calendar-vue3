<script setup>
import { ref } from 'vue'
import AppCalendar from '@/components/AppCalendar.vue'
import LocaleSwitcher from '@/components/LocaleSwitcher.vue'

const selectedDate = ref(null)
const myInitialDate = '' // Если дата не указана, будет использоваться текущая дата
const locale = ref('ru')

const handleDateSelected = (date) => {
  selectedDate.value = date
  console.log('Выбранная дата:', date)
}
</script>

<template>
  <div>
    <LocaleSwitcher v-model="locale" />

    <AppCalendar
      :initial-date="myInitialDate"
      :locale="locale"
      @date-selected="handleDateSelected"
    />
  </div>
</template>

<style scoped>
</style>