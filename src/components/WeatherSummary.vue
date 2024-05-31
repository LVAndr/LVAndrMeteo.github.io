<script setup>
import brokenClouds from '/weather-main/broken clouds.png';
import clearSky from '/weather-main/clear sky.png';
import drizzle from '/weather-main/drizzle.png';
import fewClouds from '/weather-main/few clouds.png';
import haze from '/weather-main/haze.png';
import heavyIntensityRain from '/weather-main/heavy intensity rain.png';
import lightIntensityShowerRain from '/weather-main/light intensity shower rain.png';
import lightRain from '/weather-main/light rain.png';
import lightSnow from '/weather-main/light snow.png';
import mist from '/weather-main/mist.png';
import moderateRain from '/weather-main/moderate rain.png';
import overcastClouds from '/weather-main/overcast clouds.png';
import rain from '/weather-main/rain.png';
import scatteredClouds from '/weather-main/scattered clouds.png'
import snow from '/weather-main/snow.png'
import thunderstorm from '/weather-main/thunderstorm.png'
import {capitalizeFirstLetter} from "../utils/index.js";

const images = {
  'broken clouds': brokenClouds,
  'clear sky': clearSky,
  'drizzle': drizzle,
  'few clouds': fewClouds,
  'haze': haze,
  'heavy intensity rain': heavyIntensityRain,
  'light intensity shower rain': lightIntensityShowerRain,
  'light rain': lightRain,
  'light snow': lightSnow,
  'mist': mist,
  'moderate rain': moderateRain,
  'overcast clouds': overcastClouds,
  'rain': rain,
  'scattered clouds': scatteredClouds,
  'snow': snow,
  'thunderstorm': thunderstorm
}

const props = defineProps({
  weatherInfo: {
    type: [Object, null],
    required: true
  }
})

const today = new Date().toLocaleString('en-En', {weekday: 'short', year: 'numeric', month: 'long', day: 'numeric'})
</script>
<!--style="background-image: url('../assets/img/weather-main/thunderstorm.png');"-->
<template>
  <div class="summary">
    <div class="pic-main">
      <img :src="images[weatherInfo?.weather[0]?.description]" alt="">
    </div>
    <div class="weather">
      <div class="temp">
        {{Math.round(weatherInfo?.main?.temp)}} °C
      </div>
      <div class="weather-desc text-block">
        {{capitalizeFirstLetter(weatherInfo?.weather[0]?.description)}}
      </div>
    </div>
    <div class="city text-block">
      {{weatherInfo?.name}},
      {{weatherInfo?.sys?.country}}
    </div>
    <div class="date text-block">
      {{today}}
    </div>
  </div>
</template>

<style scoped lang="sass">
@import "../assets/styles/main"

.pic-main>img
  width: 60px
  height: 60px
  margin: 20px 0 12px
  background-repeat: no-repeat
  background-position: 50% 50%
  background-size: contain

.city
  font-size: 24px

.weather
  margin: 0 0 20px
  padding: 20px 0
  border-bottom: 1px solid rgba(255, 255, 255, 0.4)

.temp
  padding-bottom: 8px
  font-size: 32px

.text-block
  position: relative
  padding-left: 24px
  padding-bottom: 8px
  font-size: 14px

  &::before
    content: ''
    position: absolute
    top: 0
    left: 0
    width: 20px
    height: 20px
    margin-right: 6px
    background-repeat: no-repeat
    background-position: 50% 50%
    background-size: contain

.weather-desc

  &::before
    background-image: url('../assets/img/weather.svg')

.city

  &::before
    background-image: url('../assets/img/location.svg')

.date

  &::before
    left: 2px
    width: 15px
    height: 15px
    background-image: url('../assets/img/calendar.svg')

</style>