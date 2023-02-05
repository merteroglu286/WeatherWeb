<template>
  <div id="app">
    <div class="background">
      <div class="container">
        <input type="text" class="form-control mt-2 mb-4 py-2" placeholder="Şehir Ara" v-model="query" @keypress="fetchWeather" aria-label="Username" aria-describedby="basic-addon1" style="text-align: center; font-size: 24px;">
        
      </div>
    
      <div class="container" v-if="(typeof weather.main != 'undefined')">
        <div class="row">
          <div class="col-sm mx-1 py-5 h5" style="text-align: center; background-color: rgba(0, 0, 0, 0.20); color: white; border-radius: 24px;"><strong class="h3">Hava Durumu</strong><br/><br/>{{weather.weather[0].description}}</div>
          <div class="col-sm mx-1 py-5 h5" style="text-align: center; background-color: rgba(0, 0, 0, 0.20); color: white; border-radius: 24px;"><strong class="h3">Sıcaklık</strong><br/><br/>{{Math.round(weather.main.temp)}}°C</div>
          <div class="col-sm mx-1 py-5 h5" style="text-align: center; background-color: rgba(0, 0, 0, 0.20); color: white; border-radius: 24px;"><strong class="h3">Rüzgar Hızı</strong><br/><br/>{{weather.wind.speed}} m/s</div>
          <div class="col-sm mx-1 py-5 h5" style="text-align: center; background-color: rgba(0, 0, 0, 0.20); color: white; border-radius: 24px;"><strong class="h3">Nem</strong><br/><br/>{{weather.main.humidity}}%</div>
        </div>
      </div>

      <div class="container">
        <ul class="nav nav-tabs mt-4">
            <li class="nav-item mx-2">
                <a class="nav-link active text-capitalize fs-6" data-bs-toggle="tab" style="color: black;" href="#bugun">Bugün</a>
            </li>
            <li class="nav-item mx-2">
                <a class="nav-link text-capitalize fs-6" data-bs-toggle="tab" style="color: black;" href="#yarin">Yarın</a>
            </li>
            <li class="nav-item mx-2">
                <a class="nav-link text-capitalize fs-6" data-bs-toggle="tab" style="color: black;" href="#ucuncu">{{getDayOfWeek(date+2)}}</a>
            </li>
            <li class="nav-item mx-2">
                <a class="nav-link text-capitalize fs-6" data-bs-toggle="tab" style="color: black;" href="#dorduncu">{{getDayOfWeek(date+3)}}</a>
            </li>
            <li class="nav-item mx-2">
                <a class="nav-link text-capitalize fs-6" data-bs-toggle="tab" style="color: black;" href="#besinci">{{getDayOfWeek(date+4)}}</a>
            </li>
        </ul>

        <div class="tab-content">
            <div class="tab-pane fade show active mt-3" id="bugun">
                <div class="row">
                    <div class="col">
                      <p>00:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[0].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[0].weather[0].description }}</p>
                    </div>
                    <div class="col">
                      <p>03:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[1].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[1].weather[0].description }}</p>
                    </div>
                    <div class="col">
                      <p>06:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[2].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[2].weather[0].description }}</p>
                    </div>
                    <div class="col">
                      <p>09:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[3].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[3].weather[0].description }}</p>
                    </div>
                </div>
                <div class="row">
                  <div class="col">
                      <p>12:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[4].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[4].weather[0].description }}</p>
                    </div>
                    <div class="col">
                      <p>15:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[5].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[5].weather[0].description }}</p>
                    </div>
                    <div class="col">
                      <p>18:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[6].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[6].weather[0].description }}</p>
                    </div>
                    <div class="col">
                      <p>21:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[7].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[7].weather[0].description }}</p>
                    </div>
                </div>
            </div>
            <div class="tab-pane fade show mt-3" id="yarin">
                  <div class="row">
                    <div class="col">
                      <p>00:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[8].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[8].weather[0].description }}</p>
                    </div>
                    <div class="col">
                      <p>03:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[9].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[9].weather[0].description }}</p>
                    </div>
                    <div class="col">
                      <p>06:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[10].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[10].weather[0].description }}</p>
                    </div>
                    <div class="col">
                      <p>09:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[11].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[11].weather[0].description }}</p>
                    </div>
                </div>
                <div class="row">
                  <div class="col">
                      <p>12:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[12].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[12].weather[0].description }}</p>
                    </div>
                    <div class="col">
                      <p>15:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[13].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[13].weather[0].description }}</p>
                    </div>
                    <div class="col">
                      <p>18:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[14].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[14].weather[0].description }}</p>
                    </div>
                    <div class="col">
                      <p>21:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[15].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[15].weather[0].description }}</p>
                    </div>
                </div>
            </div>
            <div class="tab-pane fade show mt-3" id="ucuncu">
              <div class="row">
                    <div class="col">
                      <p>00:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[16].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[16].weather[0].description }}</p>
                    </div>
                    <div class="col">
                      <p>03:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[17].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[17].weather[0].description }}</p>
                    </div>
                    <div class="col">
                      <p>06:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[18].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[18].weather[0].description }}</p>
                    </div>
                    <div class="col">
                      <p>09:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[19].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[19].weather[0].description }}</p>
                    </div>
                </div>
                <div class="row">
                  <div class="col">
                      <p>12:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[20].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[20].weather[0].description }}</p>
                    </div>
                    <div class="col">
                      <p>15:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[21].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[21].weather[0].description }}</p>
                    </div>
                    <div class="col">
                      <p>18:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[22].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[22].weather[0].description }}</p>
                    </div>
                    <div class="col">
                      <p>21:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[23].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[23].weather[0].description }}</p>
                    </div>
                </div>
            </div>
            <div class="tab-pane fade show mt-3" id="dorduncu">
              <div class="row">
                    <div class="col">
                      <p>00:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[24].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[24].weather[0].description }}</p>
                    </div>
                    <div class="col">
                      <p>03:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[25].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[25].weather[0].description }}</p>
                    </div>
                    <div class="col">
                      <p>06:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[26].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[26].weather[0].description }}</p>
                    </div>
                    <div class="col">
                      <p>09:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[27].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[27].weather[0].description }}</p>
                    </div>
                </div>
                <div class="row">
                  <div class="col">
                      <p>12:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[28].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[28].weather[0].description }}</p>
                    </div>
                    <div class="col">
                      <p>15:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[29].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[29].weather[0].description }}</p>
                    </div>
                    <div class="col">
                      <p>18:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[30].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[30].weather[0].description }}</p>
                    </div>
                    <div class="col">
                      <p>21:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[31].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[31].weather[0].description }}</p>
                    </div>
                </div>
            </div>
            <div class="tab-pane fade show mt-3" id="besinci">
              <div class="row">
                    <div class="col">
                      <p>00:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[32].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[32].weather[0].description }}</p>
                    </div>
                    <div class="col">
                      <p>03:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[33].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[33].weather[0].description }}</p>
                    </div>
                    <div class="col">
                      <p>06:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[34].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[34].weather[0].description }}</p>
                    </div>
                    <div class="col">
                      <p>09:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[35].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[35].weather[0].description }}</p>
                    </div>
                </div>
                <div class="row">
                  <div class="col">
                      <p>12:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[36].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[36].weather[0].description }}</p>
                    </div>
                    <div class="col">
                      <p>15:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[37].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[37].weather[0].description }}</p>
                    </div>
                    <div class="col">
                      <p>18:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[38].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[38].weather[0].description }}</p>
                    </div>
                    <div class="col">
                      <p>21:00</p>
                      <p>Sıcaklık: {{ Math.round(forecast[39].main.temp -273.15)}} °C</p>
                      <p>Hava Durumu: {{ forecast[39].weather[0].description }}</p>
                    </div>
                </div>
            </div>

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
      date: null,
      cities: [
        { id: 1, name: 'İstanbul', temperature: null, humidity: null, windSpeed: null },
        { id: 2, name: 'Ankara', temperature: null, humidity: null, windSpeed: null },
        { id: 3, name: 'İzmir', temperature: null, humidity: null, windSpeed: null },
      ],
      weekdays: ['Pazartesi', 'Salı', 'Çarşamba', 'Perşembe', 'Cuma', 'Cumartesi','Pazar']
    };
  },
  created() {
    this.fetchWeatherData();
    this.getForecast();
    this.fetchWeatherData2();

    setInterval(() => {
      this.fetchWeatherData();
    }, 60000);
  },
  methods: {
    getDayOfWeek(date) {
      let dayOfWeek = this.weekdays[date];
      return dayOfWeek;
    },
    async fetchWeatherData2() {
      const API_KEY = '4be2e0e2378d98adbf3aa1c6fd9e4a12';
      const city = 'Istanbul';
      const url = `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${API_KEY}`;
      try {
        const response = await axios.get(url);
        const data = response.data;
        const date = new Date(data.dt * 1000);
        this.date = date.getDay();
      } catch (error) {
        console.error(error);
      }
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
    async fetchWeather(e){
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
    position: fixed;
    top: 0;
    left: 0;
    background-image: url('./assets/rainy.gif');
    background-size: cover;
  }
  .col{
    text-align: center; 
    background-color: rgba(0, 0, 0, 0.20); 
    color: white;
    margin: 24px;
    padding-top: 24px;
    padding-bottom: 24px;
    border-radius: 24px;
  }
</style>