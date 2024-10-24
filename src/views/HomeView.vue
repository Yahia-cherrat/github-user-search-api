<script>
  import { ref } from 'vue'

  import Header from '@/components/Header.vue'
  import SearchInput from '@/components/SearchInput.vue'
  import UserInfo from '@/components/UserInfo.vue'

  export default {
    components: {
      Header,
      SearchInput,
      UserInfo
    },
    setup() {
      // Ref for storing the user data returned from the Github API
      const userData = ref(null)
      
      // Function to fetch data fron the Github API
      const fetchUser = async (username) => {
        const url = `https://api.github.com/users/${username}`
        try {
          const res = await fetch(url)
          userData.value = await res.json() // Store fetched data in userData
          console.log(res)
        } catch (error) {
          console.error('Error fetching user:', error)
        }
      }

      // Return the reactive data & functions to be used in the template
      return {
        userData,
        fetchUser
      }
    }
  }

</script>

<template>
  <div class="bg-[#141C2F] h-screen flex items-center justify-center text-white font-mono">
    <div class="w-1/2 ">
      <Header/>
      <SearchInput @search="fetchUser"/>
      <UserInfo :user="userData"/>
    </div>
  </div>
</template>
