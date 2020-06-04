<template>
      <v-flex xs6>
        <v-row
          align="center"
          justify="center"
        >
        <v-col
          cols="12"
          sm="1"
          md="11"
        >
        <v-card class="elevation-12">
          <v-toolbar
            color="primary"
            dark
            flat
          >
          <v-toolbar-title>
            Songs Metadata
          </v-toolbar-title>
          </v-toolbar>
            <v-card-text>
              <div class="song">
                <v-layout>
                  <v-flex xs6>
                    <div class="song-title">
                      {{song.title}}
                    </div>
                    <div class="song-artist">
                      {{song.artist}}
                    </div>
                    <div class="song-genre">
                      {{song.genre}}
                    </div>
                    <v-btn
          color="primary"
          :to="{
           name: 'editsong',
           params: {
             songId: song.id
             }
            }">
            Edit Song
            </v-btn>
                    </v-flex>
        <v-flex xs6>
          <img class="album-image" :src="song.albumImageURL" />
          <br>
          <div class="song-album">
            {{song.album}}
          </div>
        </v-flex>
      </v-layout>
      </div>
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
.song {
  padding: 20px;
  height: 300px;
  overflow: hidden;
}
.song-title {
  font-size: 30px;
}
.song-artist {
  font-size: 24px;
}
.song-genre {
  font-size: 18px;
}
.album-image {
  width: 70%;
  margin: 0 auto;
}
</style>
