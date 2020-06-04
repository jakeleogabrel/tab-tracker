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
       <v-toolbar-title>Lyrics</v-toolbar-title>
      </v-toolbar>
        <v-card-text>
          <textarea
            v-model="song.lyrics"
            readonly
          >
          </textarea>
           </v-card-text>
            </v-card>
        </v-col>
        </v-row>
  </v-flex>
</template>

<script>
export default {
  props: [
    'song'
  ]
}
</script>

<style scoped>
textarea {
  width: 100%;
  font-family: monospace;
  border: none;
  height: 300px;
  border-style: none;
  border-color: transparent;
  overflow: auto;
  padding: 40px;
}
</style>
