<template>
  <div>
    <h1>{{ title }}</h1>
    <div v-for="(citie, x) in cities" :key="citie.id">
      <WeatherDetail
        v-on:addFavoriteFather="addFavoriteFather"
        :key="citie.id"
        :ciudad="citie"
      />
    </div>
  </div>
</template>

<script>
import axios from "axios";
// Usaba este minetras mi apikey se habilitaba
// import myjson from '../../dataExample/cities.json'
import WeatherDetail from "./WeatherDetail.vue";
export default {
  components: { WeatherDetail },
  data: () => {
    return {
      title: "Lista  de Ciudades",
      cities: [],
    };
  },
  mounted() {
    // 15 LLAMADAS LIMITADAS
    const apiKey = "d5acf8ceb01a29b636fb3c6663ed1a03";
    axios
      .get(
        "https://api.openweathermap.org/data/2.5/box/city?bbox=12,32,15,37,10&units=metric&APPID=" +
          apiKey
      )
      .then((response) => {
        if (response) {
          const {
            data: { list },
          } = response;
          this.cities = list;
          // localStorage.setItem("data", JSON.stringify(this.cities));
        }
        console.log(response);
      })
      .catch(function (error) {
        console.log(error);
      });
  },
  head() {
    return {
      title: "Lista de Ciudades",
    };
  },
  methods: {
    addFavoriteFather(cit) {
      let fav = JSON.parse(localStorage.getItem("favorites"));
      console.log("fav", fav);
      let arr = [];
      if (arr) {
        fav.forEach((f) => {
          if (f.id != cit.id) {
            arr.push(f);
          }
        });
      }
      arr.push(cit);
      localStorage.setItem("favorites", JSON.stringify(arr));
    },
  },
};
</script>

<style>
</style>