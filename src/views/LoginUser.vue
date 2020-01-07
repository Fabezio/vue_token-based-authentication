<template lang="pug">
div
  form(@submit.prevent='login')
    label(for='email') Email:
    input(v-model='email', name='email', type='email', value)
    label(for='password') Password:
    input(v-model='password', name='password', type='password', value)
    button(type='submit', name='button') Login
    div No account yet? then 
    router-link(to='/register') register
</template>

<script>
export default {
  data () {
    return {
      email: '',
      password: ''
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
    }
  }
}
</script>

<style scoped></style>
