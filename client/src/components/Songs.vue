<template>
<v-app id="">
    <panel title="Songs">
            <router-link
            slot="action"
            :to="{name: 'songs-create'}">
              <v-btn
              class="mx-2"
              fab dark color="indigo"
              absolute
              right>
              <v-icon dark>add</v-icon>
              </v-btn>
            </router-link>
    <v-card-text>
      <div
      v-for="song in songs"
      :key="song.id"
      class="song">
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
           name: 'viewsong',
           params: {
             songId: song.id
             }
            }">
            View Song
            </v-btn>
        </v-flex>
        <v-flex xs6>
          <img class="album-image" :src="song.albumImageURL" />
        </v-flex>
      </v-layout>
      </div>
    </v-card-text>
    </panel>
  </v-app>
</template>

<script>
import SongsService from '@/services/SongsService'
import Panel from '@/components/Panel'
export default {
  components: {
    Panel
  },
  data () {
    return {
      songs: null
    }
  },
  async mounted () {
    this.songs = (await SongsService.index()).data
  }
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
