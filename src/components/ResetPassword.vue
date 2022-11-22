<script setup>
import { useAuthStore } from "../stores/auth";
import { ref } from "vue";
import { useRoute } from "vue-router";

const route = useRoute();
const authStore = useAuthStore();

const form = ref({
  password: "",
  password_confirmation: "",
  email: route.query.email,
  token: route.params.token,
});
</script>
<template>
  <form
    class="max-w-md mx-auto bg-slate-100 p-4 rounded-lg mt-12"
    @submit.prevent="authStore.handleResetPassword(form)"
  >
    <div
      class="m-2 p-2 text-green-900 font-semibold bg-green-300 rounded-md"
      v-if="authStore.status"
    >
      {{ authStore.status }}
    </div>
    <div class="mb-6">
      <label
        for="password"
        class="block mb-2 text-sm font-medium text-gray-900 dark:text-gray-300"
        >New password</label
      >
      <input
        type="password"
        id="password"
        v-model="form.password"
        class="
          shadow-sm
          bg-gray-50
          border border-gray-300
          text-gray-900 text-sm
          rounded-lg
          focus:ring-blue-500 focus:border-blue-500
          block
          w-full
          p-2.5
          dark:bg-gray-700
          dark:border-gray-600
          dark:placeholder-gray-400
          dark:text-white
          dark:focus:ring-blue-500
          dark:focus:border-blue-500
          dark:shadow-sm-light
        "
      />
      <div v-if="authStore.errors.password" class="flex">
        <span class="text-red-400 text-sm m-2 p-2">{{
          authStore.errors.password[0]
        }}</span>
      </div>
    </div>
    <div class="mb-6">
      <label
        for="repeat-password"
        class="block mb-2 text-sm font-medium text-gray-900 dark:text-gray-300"
        >Confirm Password</label
      >
      <input
        type="password"
        id="repeat-password"
        v-model="form.password_confirmation"
        class="
          shadow-sm
          bg-gray-50
          border border-gray-300
          text-gray-900 text-sm
          rounded-lg
          focus:ring-blue-500 focus:border-blue-500
          block
          w-full
          p-2.5
          dark:bg-gray-700
          dark:border-gray-600
          dark:placeholder-gray-400
          dark:text-white
          dark:focus:ring-blue-500
          dark:focus:border-blue-500
          dark:shadow-sm-light
        "
      />
    </div>
    <button
      type="submit"
      class="
        text-white
        bg-blue-700
        hover:bg-blue-800
        focus:ring-4 focus:outline-none focus:ring-blue-300
        font-medium
        rounded-lg
        text-sm
        px-5
        py-2.5
        text-center
        dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800
      "
    >
      Reset Password
    </button>
  </form>
</template>