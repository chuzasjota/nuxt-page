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
    created(){
      axios.get(`${env.endpoint}/albums/${this.$route.params.id}`).then(albumResponse => {
        this.album = albumResponse.data
      })
      axios.get(`${env.endpoint}/albums/${this.$route.params.id}/photos`).then(photosResponse => {
        this.photos = photosResponse.data
      })      
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