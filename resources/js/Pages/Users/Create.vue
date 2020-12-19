<template>
  <div>
    <h1 class="mb-8 font-bold text-3xl">
      <inertia-link class="text-indigo-400 hover:text-indigo-600" :href="route('users')">Пользователи</inertia-link>
      <span class="text-indigo-400 font-medium">/</span> Создать
    </h1>
    <div class="bg-white rounded shadow overflow-hidden max-w-3xl">
      <form @submit.prevent="submit">
        <div class="p-8 -mr-6 -mb-8 flex flex-wrap">
          <text-input v-model="form.first_name" :error="errors.first_name" class="pr-6 pb-8 w-full lg:w-1/2" label="Имя" />
          <text-input v-model="form.last_name" :error="errors.last_name" class="pr-6 pb-8 w-full lg:w-1/2" label="Фамилия" />
          <text-input v-model="form.email" :error="errors.email" class="pr-6 pb-8 w-full lg:w-1/2" label="Эл. почта" />
          <text-input v-model="form.password" :error="errors.password" class="pr-6 pb-8 w-full lg:w-1/2" type="password" autocomplete="new-password" label="Пароль" />
          <select-input v-model="form.owner" :error="errors.owner" class="pr-6 pb-8 w-full lg:w-1/2" label="Владелец">
            <option :value="true">Да</option>
            <option :value="false">Нет</option>
          </select-input>
          <file-input v-model="form.photo" :error="errors.photo" class="pr-6 pb-8 w-full lg:w-1/2" type="file" accept="image/*" label="Фото" />
        </div>
        <div class="px-8 py-4 bg-gray-100 border-t border-gray-200 flex justify-end items-center">
          <loading-button :loading="sending" class="btn-indigo" type="submit">Создать пользователя</loading-button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import Layout from '@/Shared/Layout'
import LoadingButton from '@/Shared/LoadingButton'
import SelectInput from '@/Shared/SelectInput'
import TextInput from '@/Shared/TextInput'
import FileInput from '@/Shared/FileInput'

export default {
  metaInfo: { title: 'Создать пользователя' },
  layout: Layout,
  components: {
    LoadingButton,
    SelectInput,
    TextInput,
    FileInput,
  },
  props: {
    errors: Object,
  },
  remember: 'form',
  data() {
    return {
      sending: false,
      form: {
        first_name: null,
        last_name: null,
        email: null,
        password: null,
        owner: false,
        photo: null,
      },
    }
  },
  methods: {
    submit() {
      const data = new FormData()
      data.append('first_name', this.form.first_name || '')
      data.append('last_name', this.form.last_name || '')
      data.append('email', this.form.email || '')
      data.append('password', this.form.password || '')
      data.append('owner', this.form.owner ? '1' : '0')
      data.append('photo', this.form.photo || '')

      this.$inertia.post(this.route('users.store'), data, {
        onStart: () => this.sending = true,
        onFinish: () => this.sending = false,
      })
    },
  },
}
</script>
