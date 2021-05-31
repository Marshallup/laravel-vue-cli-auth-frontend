<template>
  <form @submit.prevent="submit">
    <h1 class="h3 mb-3 fw-normal">Please register</h1>

    <div class="form-floating">
      <input
        v-model="data.name"
        type="text" class="form-control" placeholder="Name">
    </div>
    <div class="form-floating">
      <input
        v-model="data.email"
        type="email"
        class="form-control"
        placeholder="name@example.com"
      >
    </div>
    <div class="form-floating">
      <input
        v-model="data.password"
        type="password"
        class="form-control"
        placeholder="Password"
      >
    </div>

    <button class="w-100 btn btn-lg btn-primary" type="submit">Sign in</button>
  </form>
</template>

<script>
export default {
  name: 'Register',
  data() {
    return {
      data: {
        name: '',
        email: '',
        password: '',
      },
    };
  },
  methods: {
    async submit() {
      await fetch('http://127.0.0.1:8000/api/register', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify(this.data),
      });

      await this.$router.push('/login');
    },
  },
};
</script>

<style scoped>

</style>
