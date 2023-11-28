<template>
    <MainLayout>
        <div id="IndexPage" class="w-full overflow-auto">
            <div class="mx-auto max-w-[500px] overflow-hidden">
                <div id="Posts" class="px-4 max-w-[600px] mx-auto" v-if="isPosts">
                    <div v-for="post in userStore.posts" :key="post" class="">
                        {{ post }}
                    </div>
                </div>
            </div>
        </div>
    </MainLayout>
</template>

<script setup>
import { useUserStore } from '~/stores/user';
import MainLayout from '../layouts/MainLayout.vue';
const userStore = useUserStore()
// const user = useSupabaseUser() 
const isPosts = true
</script>
