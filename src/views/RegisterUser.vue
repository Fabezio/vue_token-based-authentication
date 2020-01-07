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
</template>

<script>
export default {
  data () {
    return {
      name: '',
      email: '',
      password: ''
    }
  },
  methods: {
    register () {
      this.$store.dispatch('register', {
        name: this.name,
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
