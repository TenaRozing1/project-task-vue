<template>
  <nav class="bg-gray-800 p-4 text-white flex justify-between items-center">
    <img src="/alien.png" alt="Alien image" class="w-10 h-10">
    <div class="hidden md:flex items-center gap-x-5">
      <nuxt-link to="/" class="text-lg font-medium hover:underline hover:text-indigo-200 duration-500">Home</nuxt-link>
      <nuxt-link to="/add-employee" class="text-lg font-medium hover:underline hover:text-indigo-200 duration-500">Add
        Employee</nuxt-link>
    </div>
    <div class="md:hidden flex items-center">
      <button @click="toggleMenu" class="text-lg font-medium hover:text-indigo-200 duration-500">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7" />
        </svg>
      </button>
    </div>
    <div v-if="isMobileMenuOpen"
      class="md:hidden fixed inset-0 bg-gray-900 z-50 flex flex-col items-center pt-16 uppercase ml-16">
      <nuxt-link @click.native="toggleMenu" to="/"
        class="md:text-lg font-medium mb-4 hover:underline hover:text-indigo-200 duration-500">Home</nuxt-link>
      <nuxt-link @click.native="toggleMenu" to="/add-employee"
        class="md:text-lg font-medium mb-4 hover:underline hover:text-indigo-200 duration-500">Add Employee</nuxt-link>
      <button @click="toggleMenu"
        class="font-medium hover:text-indigo-200 duration-500 absolute top-0 right-0 mr-10 mt-10">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
        </svg>
      </button>
    </div>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      isMobileMenuOpen: false
    };
  },
  methods: {
    toggleMenu() {
      this.isMobileMenuOpen = !this.isMobileMenuOpen;
    }
  }
};
</script>
