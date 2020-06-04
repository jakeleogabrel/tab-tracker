<template>
  <v-content>
    <v-layout>
        <song-metadata :song="song"/>
        <youtube-view :youtubeId="song.youtubeId"/>
    </v-layout>
    <v-layout>
        <tabs-view :song="song"/>
        <lyrics-view :song="song"/>
    </v-layout>
    </v-content>
</template>

<style scoped>

</style>

<script>
import SongMetadata from '@/components/ViewSong/SongMetadata'
import YoutubeView from '@/components/ViewSong/YoutubeView'
import TabsView from '@/components/ViewSong/TabsView'
import LyricsView from '@/components/ViewSong/LyricsView'
import SongsService from '@/services/SongsService'
import Panel from '@/components/Panel'
export default {
  data () {
    return {
      song: null
    }
  },
  async mounted () {
    const songId = this.$store.state.route.params.songId
    this.song = (await SongsService.show(songId)).data
  },
  components: {
    Panel,
    SongMetadata,
    YoutubeView,
    TabsView,
    LyricsView

  }
}
</script>

<style scoped>
</style>
