<template>
  <div id="app">
    <div class="main">
        <h1 class="main__title">Weather app</h1>
        <span class="main__sub-title">
          Check the weather in Your city
        </span>

        <form action="" class="main__form">
          <input v-model="city" type="text" name="city" class="main__input" placeholder="Write city name...">
        </form>
        <div class="main__result">
          <div class="main__city"></div>
          <div class="main__weather">
            <div class="main__temp"></div>
            <div class="main__weather-desc"></div>
            <div class="main__pressure"></div>
            <div class="main__wind"></div>
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
    };
  },
}
</script>

<style lang="scss"  src="./assets/style.scss" />
