<template>
  <div>
    <h1>Medicines</h1>
    <form @submit.prevent="addMedicine">
      <div>
        <label for="medicineName">Medicine Name:</label>
        <input type="text" id="medicineName" v-model="newMedicine.name">
      </div>
      <div>
        <label for="dosage">Dosage:</label>
        <input type="text" id="dosage" v-model="newMedicine.dosage">
      </div>
      <div>
        <label for="instructions">Instructions:</label>
        <input type="text" id="instructions" v-model="newMedicine.instructions">
      </div>
      <button type="submit">Add Medicine</button>
    </form>
    <table>
      <thead>
      <tr>
        <th>ID</th>
        <th>Name</th>
        <th>Dosage</th>
        <th>Instructions</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="medicine in medicines" :key="medicine.id">
        <td>{{ medicine.id }}</td>
        <td>{{ medicine.name }}</td>
        <td>{{ medicine.dosage }}</td>
        <td>{{ medicine.instructions }}</td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'MedicinesList',
  data() {
    return {
      medicines: [
        { id: 1, name: 'Aspirin', dosage: '500mg', instructions: 'Take one tablet daily' },
        { id: 2, name: 'Paracetamol', dosage: '650mg', instructions: 'Take one tablet every 6 hours' }
      ],
      newMedicine: {
        name: '',
        dosage: '',
        instructions: ''
      }
    };
  },
  methods: {
    addMedicine() {
      const newId = this.medicines.length + 1;
      this.medicines.push({ id: newId, ...this.newMedicine });
      this.newMedicine.name = '';
      this.newMedicine.dosage = '';
      this.newMedicine.instructions = '';
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
