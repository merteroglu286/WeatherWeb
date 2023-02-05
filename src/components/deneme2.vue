<template>
  <div id="app">
    <div class="background">
      <div class="container">
        <input type="text" class="form-control mt-5 mb-4 py-2" placeholder="Şehir Ara" v-model="query" @keypress="fetchWeather" aria-label="Username" aria-describedby="basic-addon1" style="text-align: center; font-size: 24px;">
        
      </div>
    
      <div class="container" v-if="(typeof weather.main != 'undefined')">
        <div class="row">
          <div class="col-sm mx-1 py-5 h5" style="text-align: center; background-color: rgba(0, 0, 0, 0.20); color: white; border-radius: 24px;"><strong class="h3">Hava Durumu</strong><br/><br/>{{weather.weather[0].description}}</div>
          <div class="col-sm mx-1 py-5 h5" style="text-align: center; background-color: rgba(0, 0, 0, 0.20); color: white; border-radius: 24px;"><strong class="h3">Sıcaklık</strong><br/><br/>{{Math.round(weather.main.temp)}}°C</div>
          <div class="col-sm mx-1 py-5 h5" style="text-align: center; background-color: rgba(0, 0, 0, 0.20); color: white; border-radius: 24px;"><strong class="h3">Rüzgar Hızı</strong><br/><br/>{{weather.wind.speed}} m/s</div>
          <div class="col-sm mx-1 py-5 h5" style="text-align: center; background-color: rgba(0, 0, 0, 0.20); color: white; border-radius: 24px;"><strong class="h3">Nem</strong><br/><br/>{{weather.main.humidity}}%</div>
        </div>
      </div>

      <div>
        <ul class="">
          <li class="" v-for="item in weatherData" :key="item.dt">
            {{ getDayOfWeek(item.dt) }}: {{ item.main.temp -273.15}}°C
          </li>
        </ul>
      </div>

      <div class="">
        <div class="" v-for="day in forecast" :key="day.dt">
          <p>{{ day.dt_txt }}</p>
          <p>Sıcaklık: {{ Math.round(day.main.temp -273.15)}} °C</p>
          <p>Hava Durumu: {{ day.weather[0].description }}</p>
        </div>
      </div>


      <div class="row fixed-bottom m-3">
        <div class="col-1"></div>
        <div class="col-md py-4" style="text-align: center; background-color: rgba(255, 255, 255, 0.4); border-radius: 16px;">

          <h2>{{ cities[0].name }}</h2>
          <p>Sıcaklık: {{ Math.round(cities[0].temperature) }}°C</p>
          <p>Nem: {{ cities[0].humidity }}%</p>
          <p>Rüzgar Hızı: {{ cities[0].windSpeed }} m/s</p>

        </div>
        <div class="col-1"></div>
        <div class="col-md py-4" style="text-align: center; background-color: rgba(255, 255, 255, 0.4); border-radius: 16px;">

          <h2>{{ cities[1].name }}</h2>
          <p>Sıcaklık: {{ Math.round(cities[1].temperature) }}°C</p>
          <p>Nem: {{ cities[1].humidity }}%</p>
          <p>Rüzgar Hızı: {{ cities[1].windSpeed }} m/s</p>

        </div>
        <div class="col-1"></div>
        <div class="col-md py-4" style="text-align: center; background-color: rgba(255, 255, 255, 0.4); border-radius: 16px;">

          <h2>{{ cities[2].name }}</h2>
          <p>Sıcaklık: {{ Math.round(cities[2].temperature) }}°C</p>
          <p>Nem: {{ cities[2].humidity }}%</p>
          <p>Rüzgar Hızı: {{ cities[2].windSpeed }} m/s</p>

        </div>
        <div class="col-1"></div>
      </div>
    </div>
  </div>

  

</template>

<script>
import axios from 'axios';

const API_KEY = '4be2e0e2378d98adbf3aa1c6fd9e4a12';
const API_URL = `http://api.openweathermap.org/data/2.5/weather?appid=${API_KEY}`;
const KELVIN_TO_CELSIUS_OFFSET = 273.15;

export default {
  name: 'app',
  data() {
    return {
      api_key : '4be2e0e2378d98adbf3aa1c6fd9e4a12',
      url_base : "https://api.openweathermap.org/data/2.5/",
      query: "",
      weather: {},
      forecast: [],
      cities: [
        { id: 1, name: 'İstanbul', temperature: null, humidity: null, windSpeed: null },
        { id: 2, name: 'Ankara', temperature: null, humidity: null, windSpeed: null },
        { id: 3, name: 'İzmir', temperature: null, humidity: null, windSpeed: null },
      ],
      weatherData: [],
      weekdays: ['Pazartesi', 'Salı', 'Çarşamba', 'Perşembe', 'Cuma', 'Cumartesi','Pazar']
    };
  },
  created() {
    this.fetchWeatherData();
    this.getForecast();

    setInterval(() => {
      this.fetchWeatherData();
    }, 60000);
    
  },
  methods: {
    getDayOfWeek(unixTimestamp) {
      let dateObject = new Date(unixTimestamp * 1000);
      let dayOfWeek = this.weekdays[dateObject.getDay()];
      return dayOfWeek;
    },
    fetchWeatherData() {
      this.cities.forEach(city => {
        axios
          .get(`${API_URL}&q=${city.name}`)
          .then(response => {
            const data = response.data;
            city.temperature = data.main.temp - KELVIN_TO_CELSIUS_OFFSET;
            city.humidity = data.main.humidity;
            city.windSpeed = data.wind.speed;
          })
          .catch(error => {
            console.error(error);
          });
      });
    },
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
      },
      async getForecast() {
        try {
          const response = await axios.get(
            `https://api.openweathermap.org/data/2.5/forecast?q=istanbul&appid=${this.api_key}&lang=tr`
          );
          this.forecast = response.data.list;
          this.weatherData = response.data.list;
        }catch (error) {
          console.error(error);
    }
  }
  },
};
</script>


<style>
  .background {
    width: 100%;
    height: 100%;
    /*position: fixed;*/
    top: 0;
    left: 0;
    background-image: url('./assets/rainy.gif');
    background-size: cover;
  }
</style>

<template>
  <div>
    <input type="text" v-model="city" @keydown.enter="fetchWeatherData(city); clearInput()" />
    <p v-if="weatherData">Bugünün sıcaklığı: {{ weatherData.list[0].main.temp }}°C</p>
    <p v-if="weatherData">Bugünün nem oranı: {{ weatherData.list[0].main.humidity }}%</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      weatherData: null,
      city: ''
    }
  },
  methods: {
    async fetchWeatherData(city) {
      try {
        const response = await axios.get(
          'https://api.openweathermap.org/data/2.5/forecast',
          {
            params: {
              q: city, // Kullanıcının girdiği şehir
              appid: 'API_KEY', // API anahtarınız
              units: 'metric' // Sıcaklık ölçüm birimi
            }
          }
        )
        this.weatherData = response.data
      } catch (error) {
        console.error(error)
      }
    },
    clearInput() {
      this.city = ''
    }
  }
}
</script>
