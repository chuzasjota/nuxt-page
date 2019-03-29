<template lang="html">
  <div>
    <h1>Albums</h1>
    <albumCard :album="album" v-for="album in albums" :key="album.id" />
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