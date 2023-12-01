<template>
    <div class="bottom-0 z-50 w-full h-full">
        <div class="w-full py-2">
            <div class="flex items-center justify-between">
                <div class="flex items-center text-white">
                    <img :src="post.img" class="rounded-full h-[35px]" alt="">
                    <div class="ml-2 font-medium text-[18px] ">{{ post.name }}</div>
                </div>
                <div @click="isMenu = !isMenu" class="relative">
                    <button :disabled="isDeleting"
                        class="flex items-center text-white p-1 h-[24px] w-[24px] hover:bg-gray-800 rounded-full"
                        :class="isMenu ? 'bg-gray-800' : ''">
                        <Icon v-if="!isDeleting" name="bi:three-dots" color="#fff" size="18" />
                        <Icon v-else name="eos-icons:bubble-loading" color="#fff" />
                    </button>
                    <div class="absolute right-0 z-20 mt-1 bg-gray-800 border border-gray-600" v-if="isMenu">
                        <button class="flex items-center justify-between w-full gap-2 py-1 pl-4 pr-3 text-red-500 bg-black rounded hover:bg-gray-900">
                            <div class="">delete</div>
                            <Icon name="solar:trash-bin-trash-broken" size="20"/>
                        </button>
                    </div>
                </div>
            </div>
            <div class="relative flex items-center w-full">
                <div class="w-[42px] mx-auto">
                    <div class="absolute ml-4 mt-1 top-0 w-[1px] h-full bg-gray-700"></div>
                </div>
                <div class="bg-black rounded-lg text-sm w-full font-light w-[calc(100%-50px]">
                    <div class="py-2 text-gray-300">{{ post.text }}</div>
                    <img v-if="post && post.picture" :src="post.picture" class="w-full pr-2 mx-auto mt-2 rounded" alt="">
                    <div class="absolute w-full mt-2 ml-2">
                        <button :disabled ="isLike" class="flex items-center gap-1">
                            <Icon name="mdi:cards-heart-outline" color="#fff" size="20" class="p-1 text-white rounded-full hover:bg-gray-800 " />

                        </button>
                        <div class="relative text-sm text-gray-500" >
                            <div class="">
                                <span>4</span>
                                Likes
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="relative inline-block text-gray-500 pt-1 pb-1.5">
            <div class="flex items-center" >
                <div class="flex items-center flex-wrap text-white gap-1 w-[42px]">
                    <div class="flex gap-0.5">
                        <img src="https://picsum.photos/id/17/2500/1667"  class="rounded-full w-[14px] h-[14px] mt-2" alt="">
                        <img src="https://picsum.photos/id/19/2500/1667"  class="rounded-full h-[17 px] w-[17px] mt-2" alt="">
                    </div>
                    <div class="flex items-center">
                        <img src="https://picsum.photos/id/38/1280/960" class="rounded-full h-[11px] ml-4" alt="">
                    </div>
                </div>
            </div>
        </div>
        <div class="mt-3 h-[1px] bg-gray-800 w-full" />
    </div>
</template>

<script setup>
import { useUserStore } from '#imports';
const userStore = useUserStore()

const runtimeConfig = useRuntimeConfig()
const isMenu = ref(false)
console.log("🚀 ~ file: Post.vue:69 ~ isMenu:", isMenu)
const isLike = ref(false)
const isDeleting = ref(false)

const emit = defineEmits('isDeleting')
const props = defineProps({
    post: Object
})


</script>
