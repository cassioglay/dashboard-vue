<template>
  <div class="flex justify-between">
    <h1 class="text-4xl font-black text-gray-800">
      Entre com sua conta
    </h1>
    <button
      @click="close"
      class="text-4xl text-gray-600 focus:outline-none"
    >
      &times;
    </button>
  </div>
  <div class="mt-16">
    <form @submit.prevent="handleSubmit">
      <label class="block">
        <span class="text-lg font-medium text-gray-800">E-mail</span>
        <input
        type="email"
        class="block w-full px-4 py-3 mt-1 text-lg bg-gray-100 border-2 border-transparente rounded"
        placeholder="Email..."
        v-model="state.email.value"
        :class="{'border-brand-danger': !!state.email.errorMessage}">
        <span class="block font-medium text-brand-danger"
          v-if="!!state.email.errorMessage"
        >
          {{ state.email.errorMessage }}
        </span>
      </label>
      <label class="block">
        <span class="text-lg font-medium text-gray-800">Senha</span>
        <input
        type="password"
        class="block w-full px-4 py-3 mt-1 text-lg bg-gray-100 border-2 border-transparente rounded"
        placeholder="Senha..."
        v-model="state.password.value"
        :class="{'border-brand-danger': !!state.password.errorMessage}">
        <span class="block font-medium text-brand-danger"
          v-if="!!state.password.errorMessage"
        >
          {{ state.password.errorMessage }}
        </span>
      </label>
      <button
        :disabled="state.isLoading"
        type="submit"
        :class="{
          'opacity-50': state.isLoading
        }"
        class="px-8 py-3 mt-10 text-2xl font-bold text-white rounded-full bg-brand-main focus:outline-none transition-all duration-150"
      >
        Entrar
      </button>
    </form>
  </div>
</template>

<script>
import { reactive } from 'vue'
import useModal from '../../hooks/useModal'

export default {
  setup () {
    const modal = useModal()
    const state = reactive({
      hasErrors: false,
      isLoading: false,
      email: {
        value: '',
        errorMessage: ''
      },
      password: {
        value: '',
        errorMessage: ''
      }
    })

    function handleSubmit () {

    }
    return {
      state,
      close: modal.close,
      handleSubmit
    }
  }
}
</script>

<style>

</style>
