<template lang="html">
  <div>
    <h1>{{titulo}}</h1>
    <p>{{mensaje}}</p>
  </div>
</template>

<script>
  import axios from 'axios'
  import env from '../config/env'
  export  default{
    name: 'IndexPage',
    data(){
      return {
        titulo: 'Hola mundo',
        mensaje: ''
      }
    },
    created(){
      axios.get(`${env.endpoint}/albums`).then(response=> {
        this.mensaje = response.status
      })
    }
  }
</script>

<style lang="css">

</style>