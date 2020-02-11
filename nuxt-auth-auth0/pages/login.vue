<template>
  <div class="container">
    <div>
      <logo />
      <div v-if="!this.$auth.loggedIn">
        <button class="mt-2 button--green" @click="onClickLoginButton">
          Login
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import Logo from '~/components/Logo.vue';

export default {
  components: {
    Logo
  },
  mounted() {
    if (this.$auth.loggedIn) {
      this.$router.push({
        path: '/'
      });
    }
  },
  methods: {
    onClickLoginButton(event) {
      this.$auth.loginWith('auth0');
    }
  }
};
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
  .container {
    @apply min-h-screen flex justify-center items-center text-center mx-auto;
  }
  */
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
</style>
