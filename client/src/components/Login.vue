<template>
  <v-app id="">
    <panel title="Login">
      <v-card-text>
        <v-form>
          <v-text-field
            label="Email"
            name="email"
            prepend-icon="person"
            v-model="email"
            type="email"
          ></v-text-field>
          <v-text-field
            id="password"
            label="Password"
            name="password"
            prepend-icon="lock"
            v-model="password"
            type="password"
            ></v-text-field>
         </v-form>
        </v-card-text>
          <v-alert
            dense
            outlined
            type="error"
            v-html="error"
            v-if="error">
          </v-alert>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="primary" @click="login">Login</v-btn>
        </v-card-actions>
      </panel>
  </v-app>
</template>

<script>
import Panel from '@/components/Panel'
import AuthenticationService from '@/services/AuthenticationService'
export default {
  data () {
    return {
      email: '',
      password: '',
      error: null
    }
  },
  methods: {
    async login () {
      try {
        const response = await AuthenticationService.login({
          email: this.email,
          password: this.password
        })
        this.$store.dispatch('setToken', response.data.token)
        this.$store.dispatch('setUser', response.data.user)
      } catch (error) {
        this.error = error.response.data.error
      }
    }
  },
  components: {
    Panel
  }
}
</script>
<style scoped>
</style>
