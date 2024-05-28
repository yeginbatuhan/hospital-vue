<template>
  <div>
    <h1>Departments</h1>
    <form @submit.prevent="addDepartment">
      <div>
        <label for="departmentName">Department Name:</label>
        <input type="text" id="departmentName" v-model="newDepartment.name">
      </div>
      <button type="submit">Add Department</button>
    </form>
    <table>
      <thead>
      <tr>
        <th>ID</th>
        <th>Name</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="department in departments" :key="department.id">
        <td>{{ department.id }}</td>
        <td>{{ department.name }}</td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'DepartmentsList',
  data() {
    return {
      departments: [
        { id: 1, name: 'Cardiology' },
        { id: 2, name: 'Neurology' }
      ],
      newDepartment: {
        name: ''
      }
    };
  },
  methods: {
    addDepartment() {
      const newId = this.departments.length + 1;
      this.departments.push({ id: newId, ...this.newDepartment });
      this.newDepartment.name = '';
    }
  }
};
</script>

<style scoped>
form {
  margin-bottom: 20px;
}

form div {
  margin-bottom: 10px;
}

table {
  width: 100%;
  border-collapse: collapse;
}

th, td {
  border: 1px solid #ddd;
  padding: 8px;
}

th {
  background-color: #f2f2f2;
}
</style>
