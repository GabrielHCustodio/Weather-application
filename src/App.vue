<template>
  <div class="center">
    <weather-box @bg-image="bgImage" />
  </div>
</template>

<script>
import config from "@/config/config";
import WeatherBox from "@/components/WeatherBox.vue";

export default {
  name: "App",
  data() {
    return {
      urlImage: ''
    }
  },
  components: {
    WeatherBox,
  },
  methods: {
    bgImage(city) {
      document.body.style.backgroundImage = `url("${config.apiUnsplash + city}")`;
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Ubuntu:ital,wght@0,300;0,400;0,500;0,700;1,300;1,400;1,500;1,700&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Ubuntu", sans-serif;
}

body {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100vh;
  background-color: #0093e9;
  background-image: linear-gradient(160deg, #0093e9 0%, #80d0c7 100%);
}
</style>