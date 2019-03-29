<template lang="html">
  <div>
    <h3>{{album.title}}</h3>
    <a href="#">Ver album</a>
  </div>
</template>

<script>
  export  default{
    name: 'albumCard',
    props:{
      album: Object
    }
  }
</script>

<style lang="css">

</style>