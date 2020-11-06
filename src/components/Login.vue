<template>
  <div>
    <form clas="flex flex-col items-center" @submit.prevent="login">
      <div class="flex flex-col user">
        <label for="username" class="block text-gray-700 text-sm font-bold mb-2"
          >Username</label
        >
        <input
          class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight"
          type="text"
          v-model="username"
          id="username"
        />
      </div>
      <div class="flex flex-col mt-10">
        <label for="password" class="block text-gray-700 text-sm font-bold mb-2"
          >Password</label
        >
        <input
          class="shadow appearance-none border border-red-500 rounded w-full py-2 px-3 text-gray-700"
          type="password"
          v-model="password"
        />
      </div>
      <button class="btn-blue">Sign in</button>
    </form>
    <div class="text-red-600">{{ error.message }}</div>
  </div>
</template>

<script>
import { mapActions } from "vuex";

export default {
  data() {
    return {
      username: "",
      password: "",
      email: "",
      error: "",
    };
  },
  methods: {
    ...mapActions({
      loginVue: "auth/login",
    }),
    async login() {
      try {
        await this.loginVue({
          username: this.username,
          password: this.password,
        });
      } catch (err) {
        this.err = err;
      }
    },
  },
};
</script>
