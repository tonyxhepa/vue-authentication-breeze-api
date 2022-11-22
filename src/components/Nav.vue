<script setup>
import { useAuthStore } from "../stores/auth";

const authStore = useAuthStore();
</script>
<template>
  <nav class="rounded bg-indigo-900 text-white px-2 py-2.5 sm:px-4">
    <div
      class="container mx-auto flex flex-wrap items-center justify-between"
      bis_skin_checked="1"
    >
      <a href="https://laraveller.com/" class="flex items-center">
        Laraveller
      </a>
      <button
        data-collapse-toggle="navbar-default"
        type="button"
        class="
          ml-3
          inline-flex
          items-center
          rounded-lg
          p-2
          text-sm text-gray-500
          hover:bg-gray-100
          focus:outline-none focus:ring-2 focus:ring-gray-200
          dark:text-gray-400 dark:hover:bg-gray-700 dark:focus:ring-gray-600
          md:hidden
        "
        aria-controls="navbar-default"
        aria-expanded="false"
      >
        <span class="sr-only">Open main menu</span>
        <svg
          class="h-6 w-6"
          aria-hidden="true"
          fill="currentColor"
          viewBox="0 0 20 20"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            fill-rule="evenodd"
            d="M3 5a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM3 10a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM3 15a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1z"
            clip-rule="evenodd"
          ></path>
        </svg>
      </button>
      <div
        class="hidden w-full md:block md:w-auto"
        id="navbar-default"
        bis_skin_checked="1"
      >
        <ul
          class="
            mt-4
            flex flex-col
            rounded-lg
            p-4
            md:mt-0 md:flex-row md:space-x-8 md:text-sm md:font-medium
          "
        >
          <li>
            <router-link
              :to="{ name: 'Home' }"
              class="block rounded py-2 pr-4 pl-3 text-white"
              aria-current="page"
              >Home</router-link
            >
          </li>
          <template v-if="!authStore.user">
            <li>
              <router-link
                :to="{ name: 'Login' }"
                class="
                  block
                  rounded
                  py-2
                  pr-4
                  pl-3
                  text-gray-50
                  hover:bg-gray-700
                "
                >Login</router-link
              >
            </li>
            <li>
              <router-link
                :to="{ name: 'Register' }"
                class="
                  block
                  rounded
                  py-2
                  pr-4
                  pl-3
                  text-gray-50
                  hover:bg-gray-700
                  md:border-0
                "
                >Register</router-link
              >
            </li>
          </template>
          <template v-else>
            <button
              @click="authStore.handleLogout"
              class="
                block
                rounded
                py-2
                pr-4
                pl-3
                text-gray-50
                hover:bg-gray-700
                md:border-0
              "
            >
              Logout
            </button>
          </template>
        </ul>
      </div>
    </div>
  </nav>
</template>