<template>
  <form  @submit.prevent="submit">
    <h1 class="h3 mb-3 fw-normal">Please sign in</h1>

    <div class="form-floating">
      <input type="email"
             v-model="data.email"
             class="form-control"
             id="floatingInput"
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
  name: 'Login',
  data() {
    return {
      data: {
        email: '',
        password: '',
      },
    };
  },
  methods: {
    async submit() {
      const data = JSON.stringify(this.data);
      console.log(data);
      const res = await fetch('http://127.0.0.1:8000/api/login', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        // credentials: 'include',
        body: data,
      });

      console.log(await res.json());
      // await this.$router.push('/');
    },
  },
};
</script>

<style scoped>

</style>
