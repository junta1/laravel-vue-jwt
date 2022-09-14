<template>
  <div class="container">
    <form @submit.stop.prevent="submit()">
      <!-- Email input -->
      <div class="form-outline mb-4">
        <input v-model="login.email" type="email" id="form2Example1" class="form-control" />
        <label class="form-label" for="form2Example1">Email address</label>
      </div>

      <!-- Password input -->
      <div class="form-outline mb-4">
        <input v-model="login.password" type="password" id="form2Example2" class="form-control" />
        <label class="form-label" for="form2Example2">Password</label>
      </div>

      <!-- Submit button -->
      <button type="submit" class="btn btn-primary btn-block mb-4">
        Sign in
      </button>
    </form>
  </div>
</template>

<script>
export default {
  name: "Login",
  data() {
    return {
      login: {
        email: "",
        password: "",
      },
    };
  },
  methods: {
    submit() {
        console.log(this.login)
      fetch(`http://localhost:31000/api/login`, {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
          'Access': 'application/json',
        },
        body: JSON.stringify(this.login),
      })
        .then((response) => response.json())
        .then((res) => {
          console.log(res);
        });
    },
  },
};
</script>

<style lang="scss" scoped>
</style>