<template>
  <div id="app">
    <pulse-loader v-if="loading" :color="color" :width="width" :height="height" :radius="radius" :margin="margin"></pulse-loader>
    <img src="./assets/logo.png">
    <hello></hello>
  </div>
</template>

<script>
import Hello from './components/Hello'
import PulseLoader from 'vue-spinner/src/PulseLoader.vue'

export default {
  name: 'app',
  components: {
    Hello,
    PulseLoader
  },
  data () {
		return {
			color: '#3AB982',
      height: '35px',
      width: '4px',
      margin: '2px',
      radius: '2px',
      loading: false
		}
	}
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
