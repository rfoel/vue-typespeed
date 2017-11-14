<template>
  <div id="app">
    <h1>Vue Typespeed</h1>
    <board-view></board-view>
  </div>
</template>

<script>
import BoardView from "./components/BoardView.vue"

export default {
	name: "app",
	data() {
		return {
			msg: "Welcome to Your Vue.js App"
		}
	},
	components: {
		BoardView
	}
}
</script>

<style lang="scss">
#app {
	font-family: "Dosis", "Avenir", Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	color: #2c3e50;
	display: flex;
	align-items: center;
	justify-content: center;
	flex-direction: column;
  user-select: none;
}

h1 {
	font-weight: normal;
}
</style>
