<template>
  <v-layout
    column
    justify-center
    align-center
  >
    <div class="title">
      <h1>Welcome to My Radio Show</h1>
    </div>
      <div v-for="video in filteredList" v-bind:key="video">
        <div class="px-6 py-4">
          <video :src="'http://localhost:1337' + video.Video[0].url" width="840" height="540" controls></video>
        </div>
      </div>
  </v-layout>
</template>

<script>
import Logo from '~/components/Logo.vue'
import VuetifyLogo from '~/components/VuetifyLogo.vue'
import videoQuery from '~/apollo/queries/video/video.gql'

export default {
  data () {
    return {
      video: '',
      query: '',
    }
  },
  apollo: {
    videos: {
      prefetch: true,
        query: videoQuery
        }
  },
  computed: {
    filteredList() {
      return this.videos.filter(video => {
        return video
        });
    }
  },
  components: {
    Logo,
    VuetifyLogo,
    videoQuery
  }
}
</script>
