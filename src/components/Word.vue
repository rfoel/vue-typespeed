<template>
  <div class="word" :style="getPosition()" v-if="!word.hit">
			{{word.text}}
  </div>
</template>

<script>
export default {
	name: "word",
	props: ["word"],
	data() {
		return {}
	},
	mounted() {
		this.word.intervalId = setInterval(() => {
			this.moveWord()
		}, 100)
	},
	methods: {
		moveWord() {
			if (this.word.x + 5 >= 795) {
				this.$emit("gameover")
			} else {
				this.word.x += 5
			}
		},
		getPosition() {
			return `top:${this.word.y}px; transform:translateX(${this.word.x}px)`
		}
	}
}
</script>

<style lang="scss">
.word {
	position: absolute;
	color: #42b983;
	font-size: 1.5rem;
	display: block;
	transition: all .3s ease-in;
}
</style>
