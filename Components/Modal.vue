<template>
    <div id="Modal"
        class="fixed bottom-0 z-50 grid w-full h-screen bg-black bg-opacity-50 place-items-center backdrop-blur-md">
        <div class="bg-black w-full max-w-[300px] rounded-lg text-white border border-gray-600 p-2">
            <button @click="userStore.isLogoutOverlay = false"
                class="flex items-center justify-between w-full p-3 bg-black">
                <div>Close Modal</div>
                <Icon name="mdi:close" size="25" />
            </button>
            <div class="my-1 border-b border-b-gray-700" />
            <button @click="logout()" class="flex items-center justify-between w-full p-3 bg-black">
                <div>Log Out</div>
                <Icon name="ph:sign-out" size="25" />
            </button>
        </div>
    </div>
</template>

<script setup>
import { useUserStore } from '../stores/user'
const userStore = useUserStore()
// const client  = useSupabaseClient()
// const logout = () => {
//     userStore.isLogoutOverlay = false

// }
</script>

<style lang="scss" scoped></style>