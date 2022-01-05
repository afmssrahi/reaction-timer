<template>
	<h2>Chance Left: {{ 10 - clickCount }}</h2>
	<div ref="box" class="box">
		<div class="box-item" @click="stopTimer">Click Me</div>
		<div class="box-item" @click="stopTimer">Click Me</div>
		<div class="box-item" @click="stopTimer">Click Me</div>
		<div class="box-item" @click="stopTimer">Click Me</div>
		<div class="box-item" @click="stopTimer">Click Me</div>
		<div class="box-item" @click="stopTimer">Click Me</div>
		<div class="box-item" @click="stopTimer">Click Me</div>
		<div class="box-item" @click="stopTimer">Click Me</div>
		<div class="box-item" @click="stopTimer">Click Me</div>
		<div class="box-item" @click="stopTimer">Click Me</div>
		<div class="box-item" @click="stopTimer">Click Me</div>
		<div class="box-item" @click="stopTimer">Click Me</div>
	</div>
</template>

<script>
export default {
	props: ['delay'],
	data() {
		return {
			timer: null,
			reactionTime: 0,
			avgReactionTime: [],
			showBoxItemNumber: null,
			clickCount: 0,
			gameRunning: null,
			randomNum: null,
		};
	},
	mounted() {
		setTimeout(() => {
			this.showBlock = true;
			console.log(this.$refs.b);
			this.startTimer();
		}, this.delay);
	},
	methods: {
		startTimer() {
			this.timer = Date.now();
			this.randomNum = Math.round(Math.random() * 10);
			this.$refs.box.children[this.randomNum].style.visibility =
				'visible';
		},
		stopTimer() {
			this.$refs.box.children[this.randomNum].style.visibility = 'hidden';
			this.reactionTime = (Date.now() - this.timer) / 1000;
			this.avgReactionTime.push(this.reactionTime);
			this.clickCount++;
			console.log(this.clickCount);
			if (this.clickCount === 10) {
				this.$emit('end', this.reactionTime);
			} else {
				setTimeout(() => {
					// this.reactionTime =
					// 	this.avgReactionTime.reduce((a, b) => a + b, 0) /
					// 	arr.length;

					this.startTimer();
				}, this.delay);
				console.log(this.reactionTime);
				console.log(this.avgReactionTime);
			}
		},
	},
};
</script>

<style>
.block {
	width: 400px;
	border-radius: 20px;
	background: #0faf87;
	color: #fff;
	text-align: center;
	padding: 100px 0;
	margin: 40px auto;
}

.box {
	display: grid;
	grid-template-columns: repeat(4, 1fr);
	gap: 15px;
	justify-content: center;
	align-items: center;
}

.box-item:nth-child(even) {
	background-color: #444;
}

.box-item:nth-child(odd) {
	background-color: #631953;
}

.box-item {
	color: #fff;
	padding: 50px;
	border-radius: 5px;
	visibility: hidden;
}
</style>
