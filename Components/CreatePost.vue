<template>
       <div id="CreatePost" class="fixed bottom-0 z-50 w-full h-full overflow-hidden">
        <div class="w-full h-full overflow-auto text-white bg-black">
            <div class="flex items-center justify-start py-4 max-w-[500px] mx-auto border-b border-b-gray-700">
                <button 
                    @click="
                        userStore.isMenuOverlay = false;
                        clearData();
                    "
                    class="px-2 rounded-full"
                >
                    <Icon name="mdi:close" size="25"/>
                </button>
                <div class="text-[16px] font-semibold">New Thread</div>
            </div>

            <div id="Post" class="z-40 bottom-0 max-h-[100vh-200px] w-full px-3 max-w-[500px] mx-auto">
                <div class="w-full py-2 ">
                    <div class="flex items-center">
                        <div v-if="user" class="flex items-center text-white">
                            <img class="rounded-full h-[35px]" :src="user.identities[0].identity_data.avatar_url">
                            <div class="ml-2 font-semibold text-[18px]">{{ user.identities[0].identity_data.full_name }}</div>
                        </div>
                    </div>
                    <div class="relative flex items-center w-full">
                        <div class="w-[42px] mx-auto">
                            <div class="absolute ml-4 mt-1 top-0 w-[1px] bg-gray-700 h-full" />
                        </div>
                        <div class="bg-black rounded-lg w-[calc(100%-50px)] text w-full font-light">
                            <div class="w-full pt-2 text-gray-300 bg-black">
                                <textarea
                                    v-model="text" 
                                    style="resize: none;" 
                                    placeholder="Start a thread..." 
                                    id="textarea" 
                                    @input="adjustTextareaHeight()" 
                                    class="w-full bg-black outline-none"
                                ></textarea>
                            </div>

                            <div class="w-full ">
                                <div class="flex flex-col gap-2 py-1">

                                    <div v-if="fileDisplay">
                                        <img class="w-full mx-auto mt-2 mr-2 rounded-lg" :src="fileDisplay" />
                                    </div>
                                    
                                    <label for="fileInput">
                                        <Icon name="clarity:paperclip-line" color="#ffffff" size="25"/>
                                        <input 
                                            ref="file" 
                                            type="file" 
                                            id="fileInput"
                                            @input="onChange" 
                                            hidden 
                                            accept=".jpg,.jpeg,.png" 
                                        />
                                    </label>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <div v-if="fileDisplay" class="mt-16"></div>
            <button 
                v-if="text" 
                :disabled="isLoading"
                @click="createPost"
                class="fixed bottom-0 inline-block float-right w-full p-2 p-4 text-lg font-bold bg-black border-t border-t-gray-700"
                :class="isLoading ? 'text-gray-600' : 'text-blue-600'"
            >
                <div v-if="!isLoading">Post</div>
                <div v-else class="flex items-center justify-center gap-2">
                    <Icon name="eos-icons:bubble-loading" size="25" /> 
                    Please wait...
                </div>
            </button>
        </div>
    </div>
</template>

<script setup>
import {v4 as uuidv4 } from "uuid"
import { useUserStore } from '#imports';
const userStore = useUserStore()
const text = ref(null)
const isLoading = ref(false)

const adjustTextareaHeight = () => {
    const textarea = document.getElementById('textarea');
    textarea.style.height = 'auto';
    textarea.style.height = `${textarea.scrollHeight}px`;
}
const fileDisplay = ref(null)
const file = ref(null)
const fileData = ref(null)
const onChange = (e) => {
    file.value = e.target.files[0]
    fileDisplay.value = URL.createObjectURL(file.value)
}
const createData = () => {
    text.value = null
    fileDisplay.value = null
    file.value = null
    fileData.value = null
}


</script>
