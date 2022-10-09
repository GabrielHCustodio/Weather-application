<template>
  <div class="container">
    <div class="form">
      <h3>Confira o clima na sua cidade:</h3>
      <div class="form-input-container">
        <input type="text" placeholder="Digite o nome da cidade" />
        <button>
          <i class="fa-solid fa-magnifying-glass"></i>
        </button>
      </div>
    </div>

    <div class="weather-data">
      <h2>
        <i class="fa-solid fa-location-dot"></i>
        <span>Poços de Caldas</span>
        <img id="country" src="https://countryflagsapi.com/png/brazil" alt="Bandeira do país" />
      </h2>
      
      <p id="temperature"><span>38</span>&deg;C</p>

      <div class="description-container">
        <p id="description">Ensolarado</p>
        <img src="https://openweathermap.org/img/wn/01d.png" alt="Condição do tempo" />
      </div>

      <div class="container-details">
        <p id="umidity">
          <i class="fa-solid fa-droplet"></i>
          <span>48%</span>
        </p>
        <p>
          <i class="fa-solid fa-wind"></i>
          <span>2.8Km/h</span>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "WeatherBox",
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
  padding: .8rem;
  border: none;
  border-radius: 4px;
  flex: 1;
  outline: none;
}

.form button {
  padding: .8rem;
  min-width: 50px;
  background: #8dd0f5;
  color: #fdfdfd;
  border: none;
  border-radius: 4px;
  margin-left: 8px;
  cursor: pointer;
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

.container-details #umidity {
  border-right: 1px solid #fff;
  margin: 0.6rem;
  padding: 0.6rem;
}
</style>