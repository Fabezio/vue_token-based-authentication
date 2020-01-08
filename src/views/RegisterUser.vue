<template lang="pug">
div
  form(@submit.prevent='register')
    label(for='name') Name:
    input(v-model='name', name='name', type='text', value)
    label(for='email') Email:
    input(v-model='email', name='email', type='email', value)
    label(for='password') Password:
    input(v-model='password', name='password', type='password', value)
    button(type='submit', name='button') Register
    ul
      li(v-for='(error, index) in errors' :key='index') {{error}}

  div Already have an account?
  div Login
    span &nbsp;
      router-link(to='/login') there
</template>

<script>
export default {
  data () {
    return {
      name: '',
      email: '',
      password: '',
      errors: null
    }
  },
  methods: {
    register () {
      this.$store
        .dispatch('register', {
          name: this.name,
          email: this.email,
          password: this.password
        })
        .then(() => {
          this.$router.push({ name: 'dashboard' })
        })
        .catch((err) => {
          this.errors = err.response.data.errors
        })
    }
  }
}
</script>

<style scoped></style>
