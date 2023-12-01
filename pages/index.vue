<template>
    <MainLayout>
        <div id="IndexPage" class="w-full overflow-auto">
            <div class="mx-auto max-w-[500px] overflow-hidden">
                <div id="Posts" class="px-4 max-w-[600px] mx-auto" v-if="isPosts">
                    <div class="text-white  " v-for="post in posts" :key="post">
                        <Post :post="post" @isDeleted="posts = []" />
                    </div>
             
                </div>
            </div>
        </div>
    </MainLayout>
</template>

<script setup>
import { useUserStore } from '~/stores/user';
import MainLayout from '../layouts/MainLayout.vue';
import Post from './../Components/Post.vue'
const userStore = useUserStore()
// const user = useSupabaseUser() 
const posts = ref([])
const isPosts = ref(true)
const isLoading = ref(false)

onBeforeMount(() => {
    posts.value = [
        {
            name: "Arezoo Moradi",
            image: 'https://placehold.co/100',
            text: "This is the title",
            picture: "https://placehold.co/500"
        }
    ]
})
</script>
