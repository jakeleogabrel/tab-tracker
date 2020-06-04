<template>
    <div>
      <v-app-bar
        color="blue darken-1"
        dense
        dark
        fixed
      >
        <v-toolbar-title>
           <router-link to="/" tag="span">
           <span class="home">
                   Tab Tracker
           </span>
           </router-link>
        </v-toolbar-title>

        <v-toolbar-items>
          <v-btn text small color="white">
          <router-link
          :to="{name: 'songs'}"
          tag="span">
            BROWSE
          </router-link>
          </v-btn>
        </v-toolbar-items>

        <v-spacer></v-spacer>

        <v-toolbar-items>
            <v-btn
            v-if="!$store.state.isUserLoggedIn"
            text small color="white">
                 <router-link
                 :to="{name: 'login'}"
                 tag="span">
                     LOGIN
                 </router-link>
             </v-btn>
             <v-btn
             v-if="!$store.state.isUserLoggedIn"
             text small color="white">
                 <router-link
                 :to="{name: 'register'}"
                 tag="span">
                     SIGN UP
                 </router-link>
             </v-btn>
             <v-btn
             v-if="$store.state.isUserLoggedIn"
             text small color="white"
             @click="logout">
                     Logout
             </v-btn>
        </v-toolbar-items>
      </v-app-bar>
    </div>
</template>

<script>
export default {
  methods: {
    logout () {
      this.$store.dispatch('setToken', null)
      this.$store.dispatch('setUser', null)
      this.$router.push({
        name: 'root'
      })
    }
  }
}
</script>
<style scoped>
.home {
cursor: pointer;
}
</style>
