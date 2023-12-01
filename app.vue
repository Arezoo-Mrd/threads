<template>
  <div class="bg-black fixed w-[calc(100%+1px)] h-full">
    <NuxtPage />
    <CreatePost :class="[
      { 'max-h-[100vh] transition-all duration-200 ease-in visible': userStore.isMenuOverlay },
      { 'max-h-0 transition-all duration-200 ease-out invisible': !userStore.isMenuOverlay },
    ]" />
    <Modal :class="[
      { 'max-h-[100vh] transition-all duration-200 ease-in visible': userStore.isLogoutOverlay },
      { 'max-h-0 transition-all duration-200 ease-out invisible': !userStore.isLogoutOverlay },
    ]" />

  </div>
</template>


<script setup>
import { useUserStore } from '~/stores/user';
import CreatePost from './Components/CreatePost.vue'
import Modal from './Components/Modal.vue';
const userStore = useUserStore()
console.log('%c userStore', 'background: #FFF; color: #000;padding: 0.25rem;border-radius: 5px', userStore.isMenuOverlay);
</script>