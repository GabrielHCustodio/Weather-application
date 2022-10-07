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
        <img src="" alt="Bandeira do país" />
      </h2>
      
      <p><span>38</span>&deg;C</p>

      <div class="description-container">
        <p>Nublado</p>
        <img src="" alt="Condição do tempo" />
      </div>

      <div class="container-details">
        <p>
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