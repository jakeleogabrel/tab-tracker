<template>
    <v-content>
        <v-row
          align="center"
          justify="center"
        >
          <v-col
            cols="12"
            sm="6"
            md="6"
          >
            <v-card class="elevation-12">
              <v-toolbar
                color="primary"
                dark
                flat
              >
              <v-toolbar-title>{{title}}</v-toolbar-title>
              <slot name="action">
              </slot>
              </v-toolbar>
              <slot>
                  No slot content defined!
              </slot>
              </v-card>
          </v-col>
        </v-row>
    </v-content>
</template>

<script>
export default {
  props: [
    'title'
  ]
}
</script>

<style scoped>

</style>
