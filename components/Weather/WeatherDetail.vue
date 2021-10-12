<template>
<div class="card" style="width: 18rem;">
  <div class="card-body">
    <h5 class="card-title">{{ciudad.name}}</h5>
    <h6 class="card-subtitle mb-2 text-muted">{{ciudad.main ? ciudad.main.temp ? ciudad.main.temp : "0" : "0"}} Centigrados</h6>
   <button type="button" @click="addFavorite(ciudad)" class="btn btn-success">Añadir</button>
  </div>
</div></template>

<script>
export default {
  props: ["ciudad"],
  mounted() {
    console.log('THIS',this.ciudad);
  },
  methods: {
      addFavorite(cit){
        console.log('En el hijo',cit);
        this.$emit('addFavoriteFather', cit);
      }
  }
};
</script>

<style>
    .card{
        margin-top: 20px;
    }
</style>