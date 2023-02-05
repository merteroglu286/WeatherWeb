<template>
  <div>
    <input type="text" placeholder="Search..." v-model="query" @keypress="fetchWeather">
  </div>
  <div v-if="(typeof weather.main != 'undefined')">
    <p>{{weather.main.temp}}</p>
    <p>{{weather.coord}}</p>
    <p>{{weather.sys.country}}</p>
    <p>{{Math.round(weather.main.temp)}}°C</p>
    <p>{{weather.weather[0].description}}</p>
  </div>
</template>

<script>
//import Deneme1 from "./components/Deneme1.vue"
//import SearchBox from "./components/Search_Box.vue"
/*
export default{
  data() {
    //myComp : Deneme1,
    //searchBox : SearchBox
    return{
      
    }
  }


  


}
*/
export default{
    data(){
      return {
        api_key : '4be2e0e2378d98adbf3aa1c6fd9e4a12',
        url_base : "https://api.openweathermap.org/data/2.5/",
        query: "",
        weather: {},
        sehir: "İstanbul",
        tarih: "12 Aralik 2022",
        derece: "3 santigrat",
        durum : "yağmurlu",
      }
    },
    methods : {
      fetchWeather(e){
        if(e.key == "Enter"){
          fetch(`${this.url_base}weather?q=${this.query}&units=metric&APPID=${this.api_key}&lang=tr`).
          then(res =>{
            return res.json();
          }).then(this.setResults);
        }
      },
      setResults(results){
        this.weather = results
      }
    },
    computed : {},
    watch : {}
  }
</script>

<style>


</style>
