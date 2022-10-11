<template>
  <div class="container">
    <div class="form">
      <h3>Confira o clima na sua cidade:</h3>
      <div class="form-input-container">
        <input
          type="text"
          placeholder="Digite o nome da cidade"
          v-model="nameCity"
          @keyup.enter="search"
        />
        <button @click.e.prevent="search" @click="$emit('bgImage', this.nameCity)">
          <i class="fa-solid fa-magnifying-glass"></i>
        </button>
      </div>
    </div>

    <div class="weather-data hide">
      <h2>
        <i class="fa-solid fa-location-dot"></i>
        <span>{{ weather.countryName }}</span>
        <img
          id="country"
          :src="`https://countryflagsapi.com/png/${weather.countryFlag}`"
          alt="Bandeira do país"
        />
      </h2>

      <p id="temperature">
        <span>{{ weather.temperature }}</span
        >&deg;C
      </p>

      <div class="description-container">
        <p id="description">{{ weather.description }}</p>
        <img
          :src="`https://openweathermap.org/img/wn/${weather.icon}.png`"
          alt="Condição do tempo"
        />
      </div>

      <div class="container-details">
        <p id="humidity">
          <i class="fa-solid fa-droplet"></i>
          <span>{{ weather.humidity }} %</span>
        </p>
        <p>
          <i class="fa-solid fa-wind"></i>
          <span>{{ weather.wind }} Km/h</span>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import config from "@/config/config";

export default {
  name: "WeatherBox",
  emits: ['bgImage'],
  data() {
    return {
      nameCity: "",
      weather: {
        countryName: "",
        countryFlag: "",
        temperature: "",
        description: "",
        icon: "",
        humidity: "",
        wind: "",
      },
    };
  },
  methods: {
    search() {
      fetch(
        `${config.apiWeatherUrl}?q=${this.nameCity}&units=metric&appid=${config.apiWeatherKey}&lang=pt_br`
      )
        .then((response) => response.json())
        .then(
          (response) => {
            this.weather.countryName = response.name;
            this.weather.countryFlag = response.sys.country;
            this.weather.temperature = parseInt(response.main.temp);
            this.weather.description = response.weather[0].description;
            this.weather.icon = response.weather[0].icon;
            this.weather.humidity = response.main.humidity;
            this.weather.wind = response.wind.speed;
          }
        )

        let display = document.querySelector('.weather-data')
        display.classList.remove('hide')
    }
  },
};
</script>

<style scoped>
.container {
  background: #0093e9;
  box-shadow: rgba(0, 0, 0, 0.24) 0 3px 8px;
  padding: 1rem;
  border-radius: 2rem;
  color: #fdfdfd;
}

.form h3 {
  margin-bottom: 1rem;
}

.form-input-container {
  display: flex;
}

.form input {
  padding: 0.8rem;
  border: none;
  border-radius: 4px;
  flex: 1;
  outline: none;
}

.form button {
  padding: 0.8rem;
  min-width: 50px;
  background: #8dd0f5;
  color: #fdfdfd;
  border: none;
  border-radius: 4px;
  margin-left: 8px;
  cursor: pointer;
}

.hide {
  display: none;
}

.weather-data {
  border-top: 1px solid #fff;
  margin-top: 1.5rem;
  padding-top: 1.5rem;
  text-align: center;
}

.weather-data h2 {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 0.6rem;
}

.weather-data h2 i {
  font-size: 1rem;
}

.weather-data span {
  margin: 0.6rem;
}

#country {
  height: 20px;
}

#temperature {
  font-size: 4rem;
}

.description-container {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 0.6rem 0;
}

#description {
  text-transform: capitalize;
  font-weight: bold;
}

.container-details {
  display: flex;
  justify-content: center;
  align-items: center;
}

.container-details #humidity {
  border-right: 1px solid #fff;
  margin: 0.6rem;
  padding: 0.6rem;
}
</style>