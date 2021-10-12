<template>
<div class="card" style="width: 18rem; margin-left:10px">
  <div class="card-body">
    <h5 class="card-title">{{fav.name}}</h5>
    <h6 class="card-subtitle mb-2 text-muted">{{fav.main ? fav.main.temp ? fav.main.temp : "0" : "0"}} Centigrados</h6>
   <button type="button" @click="removeFavorite(fav.id)" class="btn btn-danger">Remover</button>
  </div>
</div>
</template>

<script>
export default {
  props: ["fav"],
  methods:{
      removeFavorite(id){
          let fav = JSON.parse(localStorage.getItem('favorites'));
          let arr = [];
            fav.forEach(f =>{
           if(id != f.id){
               arr.push(f);
           } 
          });
        localStorage.setItem("favorites", JSON.stringify(arr));
        this.$emit('updateList', arr);
      }
  }
}
</script>

<style>

</style>