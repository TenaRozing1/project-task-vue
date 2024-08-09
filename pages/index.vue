<template>
  <div class="p-4">
    <h1 class="text-3xl font-bold mb-4">Employees List</h1>
    <div class="mb-4">
      <input
        v-model="searchField"
        type="search"
        placeholder="Search employees"
        class="border p-2 mb-2 w-full"
      />
      <select v-model="selectedPosition" class="border p-2 mb-2 w-full">
        <option value="">All Positions</option>
        <option v-for="title in jobTitles" :key="title" :value="title">{{ title }}</option>
      </select>
    </div>

    <!-- lista zaposlenika -->
    <div>
      <div v-for="employee in filteredEmployees" :key="employee.id" class="border border-gray-300 p-4 mb-4">
        <h2 class="text-xl font-bold">{{ employee.firstName }} {{ employee.lastName }}</h2>
        <p>{{ employee.dateOfBirth }}</p>
        <p>{{ employee.jobTitle }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios }) {
    try {
      const response = await $axios.$get('/employees');
      const employees = response.data.map(employee => ({
        ...employee,
        dateOfBirth: new Date(employee.dateOfBirth).toLocaleDateString('hr-HR')
      }));
      return { employees };
    } catch (error) {
      console.error('Error fetching employees:', error);
      return { employees: [] };
    }
  },
  data() {
    return {
      searchField: '',
      selectedPosition: '',
      filteredEmployees: []
    };
  },
  computed: {
    jobTitles() {
      const titles = [...new Set(this.employees.map(employee => employee.jobTitle))];
      return titles;
    },
    filteredEmployees() {
      return this.employees.filter(employee => {
        const matchesSearch = employee.firstName.toLowerCase().includes(this.searchField.toLowerCase()) ||
                              employee.lastName.toLowerCase().includes(this.searchField.toLowerCase());
        const matchesPosition = this.selectedPosition ? employee.jobTitle === this.selectedPosition : true;
        return matchesSearch && matchesPosition;
      });
    }
  },
  watch: {
    employees() {
      this.filterEmployees();
    },
    searchField() {
      this.filterEmployees();
    },
    selectedPosition() {
      this.filterEmployees();
    }
  },
  methods: {
    filterEmployees() {
      this.filteredEmployees = this.employees.filter(employee => {
        const matchesSearch = employee.firstName.toLowerCase().includes(this.searchField.toLowerCase()) ||
                              employee.lastName.toLowerCase().includes(this.searchField.toLowerCase());
        const matchesPosition = this.selectedPosition ? employee.jobTitle === this.selectedPosition : true;
        return matchesSearch && matchesPosition;
      });
    }
  },
  mounted() {
    this.filterEmployees();
  }
}
</script>

