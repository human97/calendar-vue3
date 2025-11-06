<script setup>
defineProps({
  modelValue: {
    type: String,
    required: true
  }
})

const emit = defineEmits(['update:modelValue'])

const setLocale = (locale) => {
  emit('update:modelValue', locale)
}
</script>

<template>
  <div class="locale-switcher">
    <button @click="setLocale('ru')" :class="{ active: modelValue === 'ru' }">Русский</button>
    <button @click="setLocale('enUS')" :class="{ active: modelValue === 'enUS' }">English</button>
  </div>
</template>

<style scoped>
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