<template lang="html">
  <div class="container">
    <h1 class="title">Albums</h1>
    <div class="columns is-multiline">
      <albumCard :album="album" v-for="album in albums" :key="album.id" />
    </div>
  </div>
</template>

<script>
  import axios from 'axios'
  import env from '../config/env'
  import albumCard from '../components/albumCard'
  export  default{
    name: 'IndexPage',
    components:{
      albumCard
    },
    data(){
      return {
        albums: []
      }
    },
    created(){
      axios.get(`${env.endpoint}/albums`).then(response=> {
        this.albums = response.data
      })
    }
  }
</script>

<style lang="css">

</style>