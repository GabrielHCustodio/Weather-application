<template>
  <div class="weather-data">
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
</template>

<script>
export default {
    name: 'DisplayData',
    props: {
        weather: Object
    }
}
</script>

<style scoped>
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