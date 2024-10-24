<script>
  import { ref } from 'vue'

  export default {
    setup(props, { emit }) {
      
      // Local state for storing the input value
      const searchQuery = ref('')

      // Function to emit the search event with the query
      const handleSearch = () => {
        emit('search', searchQuery.value)
      }

      // Return local variables as properties to be used in the template
      return {
        searchQuery,
        handleSearch
      }

    }
  }
</script>

<template>
  <div class="bg-[#1F2A48] h-auto my-4 pl-5 pr-2 py-2 flex items-center justify-between rounded-lg">
    <div>
        <img src="../assets/search.svg" alt="Search">
    </div>
    <input
      v-model="searchQuery"
      type="text" 
      class="w-full p-3 text-lg mx-2 bg-transparent outline-none"
      placeholder="Search GitHub Username..."
    >
    <button 
      class="bg-[#0079FE] p-3 rounded-lg text-lg hover:bg-[#347dca] transition-all"
      @click="handleSearch"
    >
      Search
    </button>
  </div>
</template>
