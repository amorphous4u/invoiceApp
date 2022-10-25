<template>
<!--  <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </nav>
  -->
  <div id="wrapper">
    <nav class="navbar is-dark">
      
      <div class="navbar-brand">
        <router-link to="/" class="navbar-item"><strong>Invoice App</strong></router-link>
      </div>
      
      <div class="navbar-menu">
        <div class="navbar-end">
          <template v-if="$store.state.isAuthenticated">
            <router-link to="/dashboard" class="navbar-item"> Dashboard </router-link>
          </template>

          <template v-else>
            <router-link to="/" class="navbar-item"> Home </router-link>

            <div class="navbar-item">
              <div class="buttons">
                <router-link to="/sign-uo" class="button is-success"><strong> Sign Up </strong></router-link>
                <router-link to="/log-in" class="button is-light"><strong> Log In </strong></router-link>
               </div>
            </div> 
          </template>

        </div>
      </div>
    </nav>
  
    <section class="section" >
      <router-view/>
    </section>

    <footer class="footer">
      <p class="has-text-centered"> Copyright (c) 2022</p>
    </footer>
  </div>
</template>

<script>
  import axios from 'axios'

  export default {
    name: 'App',
    beforeCreate() {
      this.store.commit('initializeStore')

      const token = this.store.state.token

      if (token) {
        axios.defaults.headers.common['Authorization'] = "Token " + token
      } else {
        axios.defaults.headers.common['Authorization'] = ""
      }
    }
  }
</script>

<style lang="scss">

@import '../node_modules/bulma';

// #app {
//   font-family: Avenir, Helvetica, Arial, sans-serif;
//   -webkit-font-smoothing: antialiased;
//   -moz-osx-font-smoothing: grayscale;
//   text-align: center;
//   color: #2c3e50;
// }

// nav {
//   padding: 30px;

//   a {
//     font-weight: bold;
//     color: #2c3e50;

//     &.router-link-exact-active {
//       color: #42b983;
//     }
//   }
// }
</style>
