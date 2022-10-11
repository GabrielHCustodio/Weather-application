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
        <button @click.e.prevent="search">
          <i class="fa-solid fa-magnifying-glass"></i>
        </button>
      </div>
    </div>

    <display-data
      v-if="showData && loading === false && messageError === false"
      :weather="this.weather"
    />
    <loader v-if="loading && messageError === false" />
    <messageError v-if="messageError" />
  </div>
</template>

<script>
import config from "@/config/config";

import DisplayData from "@/components/DisplayData.vue";
import Loader from "@/components/Loader.vue";
import MessageError from "@/components/MessageError.vue";

export default {
  name: "WeatherBox",
  emits: ["bgImage"],
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
      showData: false,
      loading: false,
      messageError: false,
    };
  },
  components: {
    DisplayData,
    Loader,
    MessageError,
  },
  methods: {
    search() {
      this.loading = !this.loading;
      this.messageError = false

      fetch(
        `${config.apiWeatherUrl}?q=${this.nameCity}&units=metric&appid=${config.apiWeatherKey}&lang=pt_br`
      )
        .then((response) => response.json())
        .then((response) => {
          this.weather.countryName = response.name;
          this.weather.countryFlag = response.sys.country;
          this.weather.temperature = parseInt(response.main.temp);
          this.weather.description = response.weather[0].description;
          this.weather.icon = response.weather[0].icon;
          this.weather.humidity = response.main.humidity;
          this.weather.wind = response.wind.speed;
        })
        .catch((error) => {
          return this.messageError = true;
        });

      this.$emit("bgImage", this.nameCity);

      setTimeout(() => {
        this.loading = !this.loading;
      }, 1500);

      return (this.showData = true);
    },
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
</style>