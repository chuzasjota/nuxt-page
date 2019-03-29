<template lang="html">
  <div class="container">
    <header>
      <nuxt-link to ="/">Regresar</nuxt-link>
      <h2 class="title">{{album.title}}</h2>
    </header>
    <div class="columns is-multiline">
      <div class="column is-one-quarter" v-for="photo in photos" :key="photo.id">
        <img :src="photo.url" :alt="photo.title">
      </div>
    </div>
  </div>
</template>

<script>
  import router from 'vue-router'
  import axios from 'axios'
  import env from '../../config/env'
  export  default{
    name: 'albumId',
    data(){
      return {
        album: {},
        photos: []
      }
    },
    created: async function(){
      let albumResponse = await axios.get(`${env.endpoint}/albums/${this.$route.params.id}`)
      this.album = albumResponse.data
      let photosResponse = await axios.get(`${env.endpoint}/albums/${this.$route.params.id}/photos`)
      this.photos = photosResponse.data
    }
  }
</script>

<style scoped>
  .container{
    text-align: center;
  }

  header{
    margin: 100px 0;
  }
</style>