<template>
  <div id="board-view">
    <button @click="start">Start</button> score: {{score}}
		<board :words="words" :height="height" :width="width"></board>
    <input type="text" placeholder="Type here..." @keyup="keyup" v-model="input">
  </div>
</template>

<script>
import Board from "./Board.vue"

export default {
	name: "board-view",
	data() {
		return {
			score: 0,
			width: 800,
			height: 500,
			input: "",
			dict: ["rafael", "vue", "franco", "typespeed", "github", "topper"],
			words: []
		}
	},
	methods: {
		start() {
			let word = this.generateWord()
			this.words.push({ text: word, createdAt: Date.now(), x: -word.length * 15, y: this.getY(), hit: false })
		},
		keyup(event) {
			let input = this.input.trim()
			if (input.length && (event.keyCode == 32 || event.keyCode == 13)) {
				this.checkWord(input)
				this.input = ""
			}
		},
		generateWord() {
			return this.dict[Math.floor(Math.random() * this.dict.length)]
		},
		getY() {
			let y = Math.floor(Math.random() * this.height)
			return y
		},
		checkWord(input) {
			let word = this.words.find(word => word.text == input)
			if (word) {
				clearInterval(word.intervalId)
				word.hitAt = Date.now()
				word.hit = true
				this.score += 1				
			} else {
				this.score -= 1
			}
		}
	},
	components: {
		Board
	}
}
</script>

<style lang="scss">
input {
	font-family: "Dosis", "Avenir", Helvetica, Arial, sans-serif;
	font-size: 1.5rem;
	line-height: 1.5rem;
	width: 100%;
	padding: 10px;
	margin-top: 30px;
	box-sizing: border-box;

	&:focus {
		outline-color: #42b983;
	}
}
</style>
