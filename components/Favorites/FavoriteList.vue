<template>
<div>
<div v-for="(fav,x) in favorites" :key="fav.id">
   <favorite-detail v-on:updateList="updateList"  :fav="fav"/>
</div>
</div>
</template>

<script>
import FavoriteDetail from './FavoriteDetail.vue';
export default {
  components: { FavoriteDetail },
  data:  () => {
  return {
  favorites : [],
  }
},
methods:{
updateList(newSize) {
 this.favorites = newSize;
 }
},
created(){
let fav = JSON.parse(localStorage.getItem('favorites'));
if(fav){
  this.favorites = fav;
}
},
 
}
</script>

<style>

</style>