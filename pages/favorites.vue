<template>
<div>
<h1>Lista de favoritos</h1>
<favorite-list  style="display:flex; flex-direction:row; flex-wrap:wrap;"/>
  </div>
</template>

<script>
import FavoriteList from '../components/Favorites/FavoriteList.vue'
export default {
  components: { FavoriteList },
 head () {
    return {
      title: 'Lista de Favoritos',
    }
  },
}
</script>

<style>

</style>