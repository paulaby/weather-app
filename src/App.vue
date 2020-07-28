<template>
  <div id="app">
    <div class="main">
        <h1 class="main__title">Weather app</h1>
        <span class="main__sub-title">
          Check the weather in Your city
        </span>

        <form action="" class="main__form">
          <input v-model="city" type="text" autocomplete="off" @keypress="loadData" name="city" class="main__input" placeholder="Write city name...">
        </form>
        <div v-if="weather.main" class="main__result">
            <div class="main__city"> {{ weather.name }} </div>
            <div class="main__temp"> {{ weather.main.temp }} &#x2103;</div>
          <div class="main__weather">
            <div class="main__weather-desc"> Weather: {{ weather.weather[0].description }}</div>
            <div class="main__pressure">Pressure:  {{ weather.main.pressure }} hPa</div>
            <div class="main__wind">Wind: {{ weather.wind.speed }} meter/sec</div>
          </div>
        </div>

    </div>
  </div>
</template>

<script>

export default {
  name: 'App',

  components: {
  },

  data () {
    return {
      city: '',
      weather: {},
    };
  },

  methods: {
    async loadData (e) {
      if (e.key === 'Enter') {
        e.preventDefault();
        await fetch(`https://api.openweathermap.org/data/2.5/weather?q=${this.city}&units=metric&APPID=${process.env.VUE_APP_API_KEY}`)
        .then(res => {
          return res.json();
          })
        .then(this.setWeather);
      }
    },

    setWeather (data) {
      this.weather = data;
    },
  },
}
</script>

<style lang="scss"  src="./assets/style.scss" />
