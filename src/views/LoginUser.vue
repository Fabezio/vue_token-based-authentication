<template lang="pug">
div
  form(@submit.prevent='login')
    label(for='email') Email:
    input(v-model='email', name='email', type='email', value)
    label(for='password') Password:
    input(v-model='password', name='password', type='password', value)
    button(type='submit', name='button') Login
    p {{error}}
  div Need an account?
  div Register
    span &nbsp;
      router-link(to='/register') here
</template>

<script>
export default {
  data () {
    return {
      email: '',
      password: '',
      error: null
    }
  },
  methods: {
    login () {
      this.$store
        .dispatch('login', {
          email: this.email,
          password: this.password
        })
        .then(() => {
          this.$router.push({ name: 'dashboard' })
        })
        .catch((err) => {
          this.error = err.response.data.error
        })
    }
  }
}
</script>

<style scoped></style>
