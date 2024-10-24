<script>
    import { toRefs } from 'vue'

    export default {
        props: {
            user: Object // Accepts 'user' object as prop from parent
        },
        setup(props) {
            // Using 'toRefs' to ensure reactivity of the passed prop
            const { user } = toRefs(props)
            
            //Returning the prop to be used in the template
            return {
                user
            }
        }
    }
</script>

<template>
  <div class="bg-[#1F2A48] h-auto my-4 p-8 rounded-lg flex items-start gap-10">
    <div class="w-2/6 h-full">
        <img 
          :src="user?.avatar_url ?? '../assets/mypicture.jpg'"
          alt="GitHub User Picture" 
          class="w-[150px] h-[150px] rounded-full mx-auto object-cover"
        >
    </div>
    <div class="w-full">
        <div class="grid grid-flow-col justify-between">
            <div>
                <h1 class="text-2xl font-semibold">{{ user?.name ?? 'Unknown' }}</h1>
                <span class="text-[#095DBD] text-lg">@{{ user?.login ?? 'unknown' }}</span>
            </div>
            <div class="text-base">
                <span>Joined {{ user?.created_at.slice(0, user?.created_at.length - 10) ?? 'Unknown Date' }}</span>
            </div>
        </div>
        <div class="my-6 text-gray-400">
            {{ user?.bio ?? 'This profile has no bio.' }}
        </div>
        <div class="bg-[#141C2F] h-auto grid grid-flow-col justify-items-start px-8 py-4 rounded-lg">
            <div class="w-full">
                <h5 class="text-base font-light text-gray-300">Repos</h5>
                <span class="text-xl font-semibold">{{ user?.public_repos ?? 'unknown' }}</span>
            </div>
            <div class="w-full">
                <h5 class="text-base font-light text-gray-300">Followers</h5>
                <span class="text-xl font-semibold">{{ user?.followers ?? 'unknown' }}</span>
            </div>
            <div class="w-full">
                <h5 class="text-base font-light text-gray-300">Following</h5>
                <span class="text-xl font-semibold">{{ user?.following ?? 'unknown' }}</span>
            </div>
        </div>
        <div class="mt-6 p-2 grid grid-cols-1 lg:grid-cols-2">
            <div class="flex items-center gap-2 mt-2">
                <img src="../assets/location.svg" alt="Location">
                <p class="font-light">{{ user?.location ?? 'No Location' }}</p>
            </div>
            <div class="flex items-center gap-2 mt-2">
                <img src="../assets/twitter.svg" alt="Twitter">
                <p class="font-light">{{ user?.twitter_username ?? 'No Twitter' }}</p>
            </div>
            <div class="flex items-center gap-2 mt-2">
                <img src="../assets/link.svg" alt="Location">
                <p class="font-light">{{ user?.blog === null ? user?.blog : 'No Website' }}</p>
            </div>
            <div class="flex items-center gap-2 mt-2">
                <img src="../assets/company.svg" alt="Company">
                <p class="font-light">{{ user?.company ?? 'No Company' }}</p>
            </div>
        </div>
    </div>
  </div>
</template>