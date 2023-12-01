<template>
    <div id="AuthPage" class="w-full h-[100vh] h-screen pt-32">
        <div class="w-full">
            <div class="w-full flex items-center justify-center gap-2.5 p-2">
                <img class="w-[35px]" src="/threads-logo.png">
                <span class="text-2xl font-bold text-white">Threads</span>
            </div>

            <div class="max-w-[350px] mx-auto px-2 text-white">

                <div class="mt-4 mb-6 text-center">Login / Register</div>

                <button @click="login('github')" class="
                        flex 
                        items-center 
                        justify-center 
                        gap-3
                        p-1.5
                        w-full
                        border 
                        rounded-full
                        text-lg
                        font-semibold
                    ">
                    <div class="flex items-center justify-center gap-2">
                        <img class="w-full max-w-[30px] rounded-full" src="/github-logo.png">
                        Github
                    </div>
                </button>

            </div>
        </div>
    </div>
</template>

<script>
// const client = useSupabaseClient()
// watchEffect(() => {
//     if(user.value) {
//         navigateTo('/')
//     }
// })

const login = async (prov) => {
    // const {} = client.auth

    if (error) console.log('%c error', 'background: #FFF; color: #000;padding: 0.25rem;border-radius: 5px', error);
}
</script>

