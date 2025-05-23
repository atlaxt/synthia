<script setup lang="ts">
import signBlack from '~/assets/sign/sign_black.png'
import signWhite from '~/assets/sign/sign_white.png'

const runtimeConfig = useRuntimeConfig()
const signImage = computed(() => isDark.value ? signWhite : signBlack)
const mounted = ref<boolean>(false)
onMounted(() => mounted.value = true)
</script>

<template>
  <div class="fixed left-0 top-0 w-screen h-screen flex justify-center items-center">
    <div class="absolute inset-x-0 -top-40 -z-10 transform-gpu overflow-hidden blur-3xl sm:-top-80" aria-hidden="true">
      <div class="relative left-[calc(50%-11rem)] aspect-1155/678 w-[36.125rem] -translate-x-1/2 rotate-[30deg] bg-linear-to-tr from-primary-500 to-indigo-400 opacity-30 sm:left-[calc(50%-30rem)] sm:w-[72.1875rem]" style="clip-path: polygon(74.1% 44.1%, 100% 61.6%, 97.5% 26.9%, 85.5% 0.1%, 80.7% 2%, 72.5% 32.5%, 60.2% 62.4%, 52.4% 68.1%, 47.5% 58.3%, 45.2% 34.5%, 27.5% 76.7%, 0.1% 64.9%, 17.9% 100%, 27.6% 76.8%, 76.1% 97.7%, 74.1% 44.1%)" />
    </div>
    <div class="absolute inset-x-0 top-[calc(100%-13rem)] -z-10 transform-gpu overflow-hidden blur-3xl sm:top-[calc(100%-30rem)]" aria-hidden="true">
      <div class="relative left-[calc(50%+3rem)] aspect-1155/678 w-[36.125rem] -translate-x-1/2 bg-linear-to-tr from-primary-500 to-indigo-400 opacity-30 sm:left-[calc(50%+36rem)] sm:w-[72.1875rem]" style="clip-path: polygon(74.1% 44.1%, 100% 61.6%, 97.5% 26.9%, 85.5% 0.1%, 80.7% 2%, 72.5% 32.5%, 60.2% 62.4%, 52.4% 68.1%, 47.5% 58.3%, 45.2% 34.5%, 27.5% 76.7%, 0.1% 64.9%, 17.9% 100%, 27.6% 76.8%, 76.1% 97.7%, 74.1% 44.1%)" />
    </div>

    <div class="sm:w-auto w-full bg-gradient-to-br from-primary-600 via-primary-400 to-indigo-600 sm:p-[1px] sm:rounded-lg h-full sm:h-auto">
      <div class="sm:w-xl w-full dark:bg-secondary-950 bg-secondary-50 sm:px-12 px-4 py-8 relative sm:rounded-lg shadow-xl h-full sm:h-auto">
        <div class="flex w-full mb-12 justify-between items-center select-none">
          <div class="relative flex flex-row items-center gap-2">
            <img src="../assets/logo.png" class="h-14">
            <img src="../assets/logo.png" class="absolute blur-xl hover:blur-none duration-300 h-14">
            <div class="text-5xl font-semibold tracking-tight text-balance bg-gradient-to-r from-primary-500 to-indigo-500 bg-clip-text text-transparent">
              <label> {{ runtimeConfig.public.appName }} </label>
            </div>
          </div>
        </div>
        <div class="flex flex-row items-center gap-2 absolute top-2 right-2">
          <ToggleLanguage class="sm:fixed sm:right-2 sm:top-2" />
          <ToggleTheme variant="button" />
        </div>
        <slot />

        <a class="flex items-end justify-between mt-8" :href="runtimeConfig.public.creatorUrl" target="_blank">
          <p class="text-sm text-zinc-500">
            Made by <label class="font-bold"> Atlas Yiğit Aydın </label>
          </p>
          <img v-if="mounted" class="w-18" :src="signImage">
        </a>

        <!-- <div class="w-full flex gap-4 justify-end mt-8">
          <ToggleTheme variant="menu" />
          <ToggleTheme variant="button" />
        </div> -->
      </div>
    </div>
  </div>
</template>
