<template>
  <div class="p-4">
    <h1 class="text-3xl font-bold mb-4">Add New Employee</h1>
    <form @submit.prevent="handleSubmit">
      <div class="mb-4">
        <label for="firstName" class="block text-lg font-semibold">First Name:</label>
        <input
          v-model="firstName"
          id="firstName"
          type="text"
          required
          class="border p-2 w-full"
        />
      </div>
      <div class="mb-4">
        <label for="lastName" class="block text-lg font-semibold">Last Name:</label>
        <input
          v-model="lastName"
          id="lastName"
          type="text"
          required
          class="border p-2 w-full"
        />
      </div>
      <div class="mb-4">
        <label for="dateOfBirth" class="block text-lg font-semibold">Date of Birth:</label>
        <input
          v-model="dateOfBirth"
          id="dateOfBirth"
          type="date"
          required
          class="border p-2 w-full"
        />
      </div>
      <div class="mb-4">
        <label for="position" class="block text-lg font-semibold">Position:</label>
        <input
          v-model="position"
          id="position"
          type="text"
          required
          class="border p-2 w-full"
        />
      </div>
      <button type="submit" class="bg-blue-500 text-white p-2 w-36 rounded-lg cursor-pointer">Save</button>
    </form> 
  </div>
</template>

<script>
export default {
  data() {
    return {
      firstName: '',
      lastName: '',
      dateOfBirth: '',
      position: ''
    };
  },
  methods: {
    handleSubmit() {
      if (this.firstName && this.lastName && this.dateOfBirth && this.position) {
        console.log({
          firstName: this.firstName,
          lastName: this.lastName,
          dateOfBirth: this.dateOfBirth,
          position: this.position
        });
        this.firstName = '';
        this.lastName = '';
        this.dateOfBirth = '';
        this.position = '';
      } else {
        console.error('All fields are required!');
      }
    }
  }
}
</script>
