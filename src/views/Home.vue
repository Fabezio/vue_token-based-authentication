<template lang='pug'>
  div.home
    h1 Welcome to the Token Based Authentication course!
    div(v-if='!loggedIn') To use this app, you will need to
      span &nbsp;
        router-link(to='/login') login
      span &nbsp;
      span or
      span &nbsp;
        router-link(to='/register') register
        | .
</template>

<script>
import { authComputed } from '@/vuex/helpers.js'
export default {
  computed: {
    ...authComputed
  }
}
</script>
