<template lang='pug'>
  div.home
    h1 Welcome to the Token Based Authentication course!
    div(v-if='!loggedIn') To use this app, you will need to 
      router-link(to='/login')  login
      span  or 
      router-link(to='/register') register
</template>

<script>
import { authComputed } from '@/vuex/helpers.js'
export default {
  computed: {
    ...authComputed
  }
}
</script>
