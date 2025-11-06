# Vue 3 Календарь 

Этот проект представляет собой компонент календаря, разработанный с использованием Vue 3 Composition API (`<script setup>`) и Vite.

## Функциональность

*   **Переключение месяцев:** Навигация по месяцам вперед и назад.
*   **Выбор даты:** Возможность выбрать дату кликом мыши.
*   **Событие выбора даты:** Компонент генерирует событие `date-selected` при выборе даты, передавая выбранное значение.
*   **Начальная дата:** Можно установить начальную дату для календаря через свойство `initial-date`. Если дата не указана, используется текущая.
*   **Переключение языка:** Поддержка русского и английского языков для названий месяцев и дней недели.

## Компонент

Основной компонент - `AppCalendar.vue`.

## Зависимости

*   `vue`: Версия 3+
*   `vite`: Инструмент для сборки
*   `date-fns`: для манипуляций с датами и локализации.

# [Демонстрация](https://calendar-vue3.netlify.app/)

---

# Vue 3 Calendar

This project is a calendar component developed using Vue 3 Composition API (`<script setup>`) and Vite.

## Features

*   **Month Switching:** Navigate to the next and previous months.
*   **Date Selection:** Ability to select a date by clicking on it.
*   **Date Selection Event:** The component emits a `date-selected` event when a date is chosen, passing the selected value.
*   **Initial Date:** You can set an initial date for the calendar via the `initial-date` prop. If no date is provided, the current date is used.
*   **Language Switching:** Supports Russian and English languages for month and day names.

## Component

The main component is `AppCalendar.vue`.

## Dependencies

*   `vue`: Version 3+
*   `vite`: Build tool
*   `date-fns`: For date manipulation and localization.

# [Live Demo](https://calendar-vue3.netlify.app/)