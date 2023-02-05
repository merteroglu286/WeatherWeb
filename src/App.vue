<template>
  <div id="app">
    <div class="background">
      <div class="container">
        <input type="text" class="form-control mt-2 mb-1 py-2" placeholder="Şehir Ara" v-model="city" @keypress="getWeather" aria-label="Username" aria-describedby="basic-addon1" style="text-align: center; font-size: 24px;">
        
      </div>
     
      

      <div>
    <div class="container" v-if="weather.list">
      <h2>{{ weather.city.name }}, {{ weather.city.country }}</h2>
      <div class="row">
          <div class="col-sm mx-1 py-5 h5" style="text-align: center; background-color: rgba(0, 0, 0, 0.20); color: white; border-radius: 24px;"><strong class="h3">Hava Durumu</strong><br/><br/>{{weather.list[0].weather[0].description}}</div>
          <div class="col-sm mx-1 py-5 h5" style="text-align: center; background-color: rgba(0, 0, 0, 0.20); color: white; border-radius: 24px;"><strong class="h3">Sıcaklık</strong><br/><br/>{{Math.round(weather.list[0].main.temp)}}°C</div>
          <div class="col-sm mx-1 py-5 h5" style="text-align: center; background-color: rgba(0, 0, 0, 0.20); color: white; border-radius: 24px;"><strong class="h3">Rüzgar Hızı</strong><br/><br/>{{weather.list[0].wind.speed}} m/s</div>
          <div class="col-sm mx-1 py-5 h5" style="text-align: center; background-color: rgba(0, 0, 0, 0.20); color: white; border-radius: 24px;"><strong class="h3">Nem</strong><br/><br/>{{weather.list[0].main.humidity}}%</div>
      </div>
      
    </div>
  </div>

              

      <div class="container">
        <ul class="nav nav-tabs mt-2">
            <li class="nav-item mx-2">
                <a class="nav-link active text-capitalize fs-6" data-bs-toggle="tab" style="color: black;" href="#bugun">Bugün</a>
            </li>
            <li class="nav-item mx-2">
                <a class="nav-link text-capitalize fs-6" data-bs-toggle="tab" style="color: black;" href="#yarin">Yarın</a>
            </li>
            <li class="nav-item mx-2">
                <a class="nav-link text-capitalize fs-6" data-bs-toggle="tab" style="color: black;" href="#ucuncu">{{ getDayOfWeek(date+1) }}</a>
            </li>
            <li class="nav-item mx-2">
                <a class="nav-link text-capitalize fs-6" data-bs-toggle="tab" style="color: black;" href="#dorduncu">{{getDayOfWeek(date+2)}}</a>
            </li>
            <li class="nav-item mx-2">
                <a class="nav-link text-capitalize fs-6" data-bs-toggle="tab" style="color: black;" href="#besinci">{{getDayOfWeek(date+3)}}</a>
            </li>
        </ul>
  
        <div class="tab-content">
            <div class="tab-pane fade show active mt-3" id="bugun">
              <div class="row">
                    <div class="col" v-if="weather.list">
                      <p>00:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[0].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[0].weather[0].description }}</p>
                    </div>
                    <div class="col" v-if="weather.list">
                      <p>03:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[1].main.temp )}} °C</p>
                      <p>Hava Durumu: {{ weather.list[1].weather[0].description }}</p>
                    </div>
                    <div class="col" v-if="weather.list">
                      <p>06:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[2].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[2].weather[0].description }}</p>
                    </div>
                    <div class="col" v-if="weather.list">
                      <p>09:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[0].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[0].weather[0].description }}</p>
                    </div>
                </div>

                <div class="row">
                    <div class="col" v-if="weather.list">
                      <p>12:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[4].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[4].weather[0].description }}</p>
                    </div>
                    <div class="col" v-if="weather.list">
                      <p>15:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[5].main.temp )}} °C</p>
                      <p>Hava Durumu: {{ weather.list[5].weather[0].description }}</p>
                    </div>
                    <div class="col" v-if="weather.list">
                      <p>18:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[6].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[6].weather[0].description }}</p>
                    </div>
                    <div class="col" v-if="weather.list">
                      <p>21:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[7].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[7].weather[0].description }}</p>
                    </div>
                </div>
                
            </div>
            <div class="tab-pane fade show mt-3" id="yarin">
              <div class="row">
                    <div class="col" v-if="weather.list">
                      <p>00:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[8].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[8].weather[0].description }}</p>
                    </div>
                    <div class="col" v-if="weather.list">
                      <p>03:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[9].main.temp )}} °C</p>
                      <p>Hava Durumu: {{ weather.list[9].weather[0].description }}</p>
                    </div>
                    <div class="col" v-if="weather.list">
                      <p>06:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[10].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[10].weather[0].description }}</p>
                    </div>
                    <div class="col" v-if="weather.list">
                      <p>09:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[11].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[11].weather[0].description }}</p>
                    </div>
                </div>
                <div class="row">
                  <div class="col" v-if="weather.list">
                      <p>12:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[12].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[12].weather[0].description }}</p>
                    </div>
                    <div class="col" v-if="weather.list">
                      <p>15:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[13].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[13].weather[0].description }}</p>
                    </div>
                    <div class="col" v-if="weather.list">
                      <p>18:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[14].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[14].weather[0].description }}</p>
                    </div>
                    <div class="col" v-if="weather.list">
                      <p>21:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[15].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[15].weather[0].description }}</p>
                    </div>
                </div>
            </div>
            <div class="tab-pane fade show mt-3" id="ucuncu">
              <div class="row">
                    <div class="col" v-if="weather.list">
                      <p>00:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[16].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[16].weather[0].description }}</p>
                    </div>
                    <div class="col" v-if="weather.list">
                      <p>03:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[17].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[17].weather[0].description }}</p>
                    </div>
                    <div class="col" v-if="weather.list">
                      <p>06:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[18].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[18].weather[0].description }}</p>
                    </div>
                    <div class="col" v-if="weather.list">
                      <p>09:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[19].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[19].weather[0].description }}</p>
                    </div>
                </div>
                <div class="row">
                  <div class="col" v-if="weather.list">
                      <p>12:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[20].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[20].weather[0].description }}</p>
                    </div>
                    <div class="col" v-if="weather.list">
                      <p>15:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[21].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[21].weather[0].description }}</p>
                    </div>
                    <div class="col" v-if="weather.list">
                      <p>18:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[22].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[22].weather[0].description }}</p>
                    </div>
                    <div class="col" v-if="weather.list">
                      <p>21:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[23].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[23].weather[0].description }}</p>
                    </div>
                </div>
            </div>
            <div class="tab-pane fade show mt-3" id="dorduncu">
              <div class="row">
                    <div class="col" v-if="weather.list">
                      <p>00:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[24].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[24].weather[0].description }}</p>
                    </div>
                    <div class="col" v-if="weather.list">
                      <p>03:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[25].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[25].weather[0].description }}</p>
                    </div>
                    <div class="col" v-if="weather.list">
                      <p>06:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[26].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[26].weather[0].description }}</p>
                    </div>
                    <div class="col" v-if="weather.list">
                      <p>09:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[27].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[27].weather[0].description }}</p>
                    </div>
                </div>
                <div class="row">
                  <div class="col" v-if="weather.list">
                      <p>12:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[28].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[28].weather[0].description }}</p>
                    </div>
                    <div class="col" v-if="weather.list">
                      <p>15:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[29].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[29].weather[0].description }}</p>
                    </div>
                    <div class="col" v-if="weather.list">
                      <p>18:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[30].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[30].weather[0].description }}</p>
                    </div>
                    <div class="col" v-if="weather.list">
                      <p>21:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[31].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[31].weather[0].description }}</p>
                    </div>
                </div>
            </div>
            <div class="tab-pane fade show mt-3" id="besinci">
              <div class="row">
                    <div class="col" v-if="weather.list">
                      <p>00:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[32].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[32].weather[0].description }}</p>
                    </div>
                    <div class="col" v-if="weather.list">
                      <p>03:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[33].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[33].weather[0].description }}</p>
                    </div>
                    <div class="col" v-if="weather.list">
                      <p>06:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[34].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[34].weather[0].description }}</p>
                    </div>
                    <div class="col" v-if="weather.list">
                      <p>09:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[35].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[35].weather[0].description }}</p>
                    </div>
                </div>
                <div class="row">
                  <div class="col" v-if="weather.list">
                      <p>12:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[36].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[36].weather[0].description }}</p>
                    </div>
                    <div class="col" v-if="weather.list">
                      <p>15:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[37].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[37].weather[0].description }}</p>
                    </div>
                    <div class="col" v-if="weather.list">
                      <p>18:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[38].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[38].weather[0].description }}</p>
                    </div>
                    <div class="col" v-if="weather.list">
                      <p>21:00</p>
                      <p>Sıcaklık: {{ Math.round(weather.list[39].main.temp)}} °C</p>
                      <p>Hava Durumu: {{ weather.list[39].weather[0].description }}</p>
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
      city: "",
      weather: {},
      forecast: [],
      date: null,
      date2: null,
      yarin: null,
      sonraki1: null,
      sonraki2: null,
      sonraki3: null,
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
  computed: {
    isSunny() {
      return this.weather === 'clear';
    },
    isRainy() {
      return this.weather === 'rain';
    },
    isCloudy() {
      return this.weather === 'clouds';
    },
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
        this.date2 = date.toLocaleDateString();

        this.yarin.setDate(date2.getDate() + 1);
        yarin = date.toLocaleDateString();
        
      } catch (error) {
        console.error(error);
      }
    },
    formatDate(timestamp) {
      const date = new Date(timestamp * 1000);
      return date.toLocaleDateString('tr-tr', { year: 'numeric', month: '2-digit', day: '2-digit' });
    },
    formatTomorrow(timestamp) {
      const date = new Date(timestamp * 1000);
      date.setDate(date.getDate() + 1);
      return date.toLocaleDateString('tr-tr', { year: 'numeric', month: '2-digit', day: '2-digit' });
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
      async getForecast() {
        try {
          const response = await axios.get(
            `https://api.openweathermap.org/data/2.5/forecast?q=istanbul&appid=${this.api_key}&lang=tr`
          );
          this.forecast = response.data.list;
        }catch (error) {
          console.error(error);
    }
  },
  async getWeather(e) {
    if(e.key == "Enter"){
      const API_KEY = '4be2e0e2378d98adbf3aa1c6fd9e4a12';
      const API_ENDPOINT = `https://api.openweathermap.org/data/2.5/forecast`;
      try {
        const response = await axios.get(API_ENDPOINT, {
          params: {
            q: this.city,
            units: 'metric',
            lang: 'tr',
            appid: API_KEY
          }
        });
        this.weather = response.data;
      } catch (error) {
        console.error(error);
      }
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
    background-image: url('./assets/clouds.gif');
    background-size: cover;
  }
  .col-3{
    text-align: center; 
    background-color: rgba(0, 0, 0, 0.20); 
    color: white;
    margin: 24px;
    padding-top: 24px;
    padding-bottom: 24px;
    border-radius: 24px;
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