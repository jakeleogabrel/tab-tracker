<template>
    <v-content>
        <v-layout>
        <v-flex xs5>
        <v-row
          align="center"
          justify="center"
        >
          <v-col
            cols="12"
            sm="3"
            md="9"
          >
            <v-card class="elevation-12">
              <v-toolbar
                color="primary"
                dark
                flat
              >
              <v-toolbar-title>Add songs Metadata</v-toolbar-title>
              </v-toolbar>
                 <v-card-text>
                   <v-form>
                      <v-text-field
                       label="Title"
                       name="title"
                       prepend-icon="account_box"
                       v-model="song.title"
                       :error-messages="titleErrors"
                       type="text"
                       required
                       @input="$v.song.title.$touch()"
                       @blur="$v.song.title.$touch()"
                       ></v-text-field>
                       <v-text-field
                        label="Artist"
                        name="artist"
                        prepend-icon="person"
                        v-model="song.artist"
                        :error-messages="artistErrors"
                        type="text"
                        required
                        @input="$v.song.artist.$touch()"
                        @blur="$v.song.artist.$touch()"
                        ></v-text-field>
                        <v-text-field
                         label="Genre"
                         name="genre"
                         prepend-icon="face"
                         v-model="song.genre"
                         :error-messages="genreErrors"
                         type="text"
                         required
                        @input="$v.song.genre.$touch()"
                        @blur="$v.song.genre.$touch()"
                        ></v-text-field>
                        <v-text-field
                         label="Album"
                         name="album"
                         prepend-icon="album"
                         v-model="song.album"
                         :error-messages="albumErrors"
                         type="text"
                         required
                        @input="$v.song.album.$touch()"
                        @blur="$v.song.album.$touch()"
                        ></v-text-field>
                        <v-text-field
                         label="Album Image URL"
                         name="imageurl"
                         prepend-icon="art_track"
                         v-model="song.albumImageURL"
                         :error-messages="AlbumImageURLErrors"
                         type="text"
                         required
                        @input="$v.song.albumImageURL.$touch()"
                        @blur="$v.song.albumImageURL.$touch()"
                        ></v-text-field>
                        <v-text-field
                         label="Youtube ID"
                         name="ytId"
                         prepend-icon="video_label"
                         v-model="song.youtubeId"
                         :error-messages="youtubeIdErrors"
                         type="text"
                         required
                        @input="$v.song.youtubeId.$touch()"
                        @blur="$v.song.youtubeId.$touch()"
                        ></v-text-field>
                     </v-form>
                </v-card-text>
            </v-card>
        </v-col>
    </v-row>
    </v-flex>
        <v-flex xs7>
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
              <v-toolbar-title>Song Structure</v-toolbar-title>
              </v-toolbar>
                 <v-card-text>
                   <v-form>
                       <v-textarea
                         label="Lyrics"
                         name="lyrics"
                         prepend-icon="format_align_left"
                         v-model="song.lyrics"
                         :error-messages="LyricsErrors"
                         type="text"
                         required
                        @input="$v.song.lyrics.$touch()"
                        @blur="$v.song.lyrics.$touch()"
                        ></v-textarea>
                        <v-textarea
                         label="Tabs"
                         name="tab"
                         prepend-icon="music_note"
                         v-model="song.tab"
                         :error-messages="TabErrors"
                         type="text"
                         required
                        @input="$v.song.tab.$touch()"
                        @blur="$v.song.tab.$touch()"
                        ></v-textarea>
                    </v-form>
                </v-card-text>
                <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn color="primary" @click="save">Save song</v-btn>
                </v-card-actions>
            </v-card>
        </v-col>
    </v-row>
        </v-flex>
    </v-layout>
    </v-content>
</template>

<script>
import SongsService from '@/services/SongsService'
import { validationMixin } from 'vuelidate'
import { required } from 'vuelidate/lib/validators'

export default {
  mixins: [validationMixin],

  data () {
    return {
      song: {
        title: null,
        artist: null,
        genre: null,
        album: null,
        albumImageURL: null,
        youtubeId: null,
        lyrics: null,
        tab: null
      }
    }
  },
  validations: {
    song: {
      title: { required },
      artist: { required },
      genre: { required },
      album: { required },
      albumImageURL: { required },
      youtubeId: { required },
      lyrics: { required },
      tab: { required }
    }
  },
  computed: {
    titleErrors () {
      const errors = []
      if (!this.$v.song.title.$dirty) return errors
      !this.$v.song.title.required && errors.push('Title is required.')
      return errors
    },
    artistErrors () {
      const errors = []
      if (!this.$v.song.artist.$dirty) return errors
      !this.$v.song.artist.required && errors.push('Artist is required.')
      return errors
    },
    genreErrors () {
      const errors = []
      if (!this.$v.song.genre.$dirty) return errors
      !this.$v.song.genre.required && errors.push('Genre is required.')
      return errors
    },
    albumErrors () {
      const errors = []
      if (!this.$v.song.album.$dirty) return errors
      !this.$v.song.album.required && errors.push('Album is required.')
      return errors
    },
    AlbumImageURLErrors () {
      const errors = []
      if (!this.$v.song.albumImageURL.$dirty) return errors
      !this.$v.song.albumImageURL.required && errors.push('Album Image is required.')
      return errors
    },
    youtubeIdErrors () {
      const errors = []
      if (!this.$v.song.youtubeId.$dirty) return errors
      !this.$v.song.youtubeId.required && errors.push('Youtube ID is required.')
      return errors
    },
    LyricsErrors () {
      const errors = []
      if (!this.$v.song.lyrics.$dirty) return errors
      !this.$v.song.lyrics.required && errors.push('Lyrics is required.')
      return errors
    },
    TabErrors () {
      const errors = []
      if (!this.$v.song.tab.$dirty) return errors
      !this.$v.song.tab.required && errors.push('Tab is required.')
      return errors
    }
  },
  methods: {
    async save () {
      this.$v.$touch()
      if (!this.$v.$invalid) {
        const songId = this.$store.state.route.params.songId
        try {
          await SongsService.put(this.song)
          this.$router.push({
            name: 'songs',
            params: {
              songId: songId
            }
          })
        } catch (err) {
          console.log(err)
        }
      }
    }
  },
  async mounted () {
    const songId = this.$store.state.route.params.songId
    this.song = (await SongsService.show(songId)).data
  }
}
</script>

<style scoped>

</style>
