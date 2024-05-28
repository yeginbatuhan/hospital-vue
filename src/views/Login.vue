<template>
  <div>
    <h1>Login</h1>
    <form @submit.prevent="login">
      <div>
        <label for="username">Username:</label>
        <input type="text" id="username" v-model="username">
      </div>
      <div>
        <label for="password">Password:</label>
        <input type="password" id="password" v-model="password">
      </div>
      <button type="submit">Login</button>
    </form>
    <p v-if="error">{{ error }}</p>
  </div>
</template>

<script>
export default {
  name: 'LoginPage',
  data() {
    return {
      username: '',
      password: '',
      error: ''
    };
  },
  methods: {
    login() {
      const users = [
        { username: 'doctor1', password: 'password123', role: 'doctor' },
        { username: 'patient1', password: 'password456', role: 'patient' }
      ];

      const user = users.find(
          user => user.username === this.username && user.password === this.password
      );

      if (user) {
        this.$emit('user-logged-in', user.role);
        this.$router.push(`/${user.role}-dashboard`);
      } else {
        this.error = 'Invalid username or password';
      }
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

form label {
  display: block;
  margin-bottom: 5px;
}

form input, form button {
  width: 100%;
  padding: 8px;
  margin-bottom: 10px;
  box-sizing: border-box;
}

form button {
  background-color: #007bff;
  color: #fff;
  border: none;
  cursor: pointer;
}

form button:hover {
  background-color: #0056b3;
}

p {
  color: red;
}
</style>
