<template>
  <div id="board" :style="`width:${this.width}px; height:${this.height}px`">
    <word v-for="(word, index) of words" :word="word"  :key="index" @gameover="gameover"></word>
  </div>
</template>

<script>
import Word from "./Word.vue"

export default {
	name: "board",
	props: ["words", "width", "height"],
	data() {
		return {}
	},
	methods: {
		gameover() {
			this.words.forEach(word => {
				clearInterval(word.intervalId)
			})
		}
	},
	components: {
		Word
	}
}
</script>

<style lang="scss">
#board {
	position: relative;
	background: #2c3e50;
	overflow: hidden;
	padding-top: 50px;
	padding-right: 25px;
}
</style>
