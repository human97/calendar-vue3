<script setup>
import { ref, computed, defineEmits } from 'vue'
import {
  format,
  getDaysInMonth,
  startOfMonth,
  getDay,
  addMonths,
  subMonths,
  set,
  isSameDay,
  isToday
} from 'date-fns'

const emit = defineEmits(['date-selected'])

const currentDate = ref(new Date())
const selectedDate = ref(new Date())

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

const prevMonth = () => {
  currentDate.value = subMonths(currentDate.value, 1)
}

const nextMonth = () => {
  currentDate.value = addMonths(currentDate.value, 1)
}

const selectDay = (day) => {
  if (!day) return
  const newSelectedDate = set(currentDate.value, { date: day })
  selectedDate.value = newSelectedDate
  emit('date-selected', newSelectedDate)
}

const isDaySelected = (day) => {
  if (!day) return false
  const date = set(currentDate.value, { date: day })
  return isSameDay(date, selectedDate.value)
}

const isDayToday = (day) => {
  if (!day) return false
  const date = set(currentDate.value, { date: day })
  return isToday(date)
}
</script>

<template>
  <div class="calendar">
    <div class="header">
      <button @click="prevMonth">&lt;</button>
      <h2>{{ monthName }}</h2>
      <button @click="nextMonth">&gt;</button>
    </div>
    <div class="days-of-week">
      <div v-for="day in daysOfWeek" :key="day">{{ day }}</div>
    </div>
    <div class="days-grid">
      <div
        v-for="(day, index) in days"
        :key="index"
        class="day"
        :class="{
          'not-empty': day,
          'selected': isDaySelected(day),
          'today': isDayToday(day)
        }"
        @click="selectDay(day)"
      >
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
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  background-color: #f5f5f5;
}

.header button {
  background: none;
  border: 1px solid #ccc;
  cursor: pointer;
  padding: 5px 10px;
  border-radius: 4px;
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

.day.not-empty {
  cursor: pointer;
}

.day.not-empty:hover {
  background-color: #e9e9e9;
}

.day.selected {
  background-color: #007bff;
  color: white;
}

.day.today {
  font-weight: bold;
  border: 1px solid #007bff;
}
</style>