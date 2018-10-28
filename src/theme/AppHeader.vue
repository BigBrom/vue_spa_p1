<template>
  <nav class="nav has-shadow">
    <div class="container">
      <router-link to="/category/front-end" exact>LOGO</router-link>
      <router-link :to="{ name: 'category', params: {id: 'front-end' } }" class="nav-item is-tab">Front-end</router-link>
      <router-link :to="{ name: 'category', params: {id: 'mobile' } }" class="nav-item is-tab">Mobile</router-link>
      <router-link to="/login" class="nav-item is-tab">
        <span v-if="isAuthenticated">Login</span>
        <span v-else>Logout</span>
      </router-link>
    </div>
  </nav>
</template>
<script>
import eventBus from '../event-bus.js'
export default {
  data () {
    return {
      isAuthenticated: false
    }
  },
  created () {
    eventBus.$on('authStatusUpdate', isAuthenticated => { this.isAuthenticated = isAuthenticated })
  }
}
</script>


