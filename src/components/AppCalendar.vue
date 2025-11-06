<script setup>
import { ref, computed } from 'vue'
import { format, getDaysInMonth, startOfMonth, getDay } from 'date-fns'

const currentDate = ref(new Date())

const monthName = computed(() => format(currentDate.value, 'MMMM yyyy'))

const daysOfWeek = ['Вс', 'Пн', 'Вт', 'Ср', 'Чт', 'Пт', 'Сб']

const days = computed(() => {
  const date = currentDate.value
  const daysInMonth = getDaysInMonth(date)
  const firstDayOfMonth = getDay(startOfMonth(date))

  const daysArray = []

  for (let i = 0; i < firstDayOfMonth; i++) {
    daysArray.push('')
  }

  for (let i = 1; i <= daysInMonth; i++) {
    daysArray.push(i)
  }

  return daysArray
})
</script>

<template>
  <div class="calendar">
    <div class="header">
      <h2>{{ monthName }}</h2>
    </div>
    <div class="days-of-week">
      <div v-for="day in daysOfWeek" :key="day">{{ day }}</div>
    </div>
    <div class="days-grid">
      <div v-for="(day, index) in days" :key="index" class="day">
        {{ day }}
      </div>
    </div>
  </div>
</template>

<style scoped>
.calendar {
  font-family: sans-serif;
  width: 350px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.header {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 10px;
  background-color: #f5f5f5;
}

.days-of-week,
.days-grid {
  display: grid;
  grid-template-columns: repeat(7, 1fr);
  text-align: center;
}

.days-of-week div {
  font-weight: bold;
  padding: 10px 0;
}

.day {
  padding: 10px 5px;
  border-top: 1px solid #ccc;
}

.day:not(:nth-child(7n)) {
  border-right: 1px solid #ccc;
}

.days-grid .day:empty {
  background-color: #f9f9f9;
}
</style>