<template>
    <v-flex xs6>
            <v-row
          align="center"
          justify="center"
        >
          <v-col
            cols="12"
            sm="1"
            md="12"
          >
            <v-card class="elevation-12">
              <v-toolbar
                color="primary"
                dark
                flat
              >
              <v-toolbar-title>Youtube Link</v-toolbar-title>
              </v-toolbar>
                 <v-card-text>
                    <youtube
                    :video-id="youtubeId"
                    :player-width="600"
                    :player-height="300">
                    </youtube>
                </v-card-text>
            </v-card>
        </v-col>
    </v-row>
        </v-flex>
</template>

<script>
export default {
  props: [
    'youtubeId'
  ]
}
</script>

<style scoped>

</style>
