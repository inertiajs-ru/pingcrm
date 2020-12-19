<template>
  <div>
    <h1 class="mb-8 font-bold text-3xl">Панель инструментов</h1>
    <p class="mb-8 leading-normal">Эй, там! Добро пожаловать в Ping CRM, демонстрационное приложение, предназначенное для иллюстрации работы <a class="text-indigo-500 underline hover:text-orange-600" href="https://inertiajs.ru">Inertia.js</a>.</p>
    <div class="mb-8 flex">
      <inertia-link class="btn-indigo" href="/500">500 ошибка</inertia-link>
      <inertia-link class="btn-indigo ml-1" href="/404">404 ошибка</inertia-link>
    </div>
    <p class="leading-normal">👆 Эти ссылки предназначены для того, чтобы показать, как работает обработка ошибок в Inertia.js.</p>
  </div>
</template>

<script>
import Layout from '@/Shared/Layout'

export default {
  metaInfo: { title: 'Dashboard' },
  layout: Layout,
}
</script>
