<template>
	<h1>Result</h1>
	<p>Your Reaction Time - {{ reactionTime }} Second.</p>
	<p class="rank">{{ rank }}</p>
</template>

<script>
export default {
	props: ['reactionTime'],
	data() {
		return {
			rank: null,
		};
	},
	mounted() {
		if (this.reactionTime < 0.3) {
			this.rank = 'Ninja Reaction... :)';
		} else if (this.reactionTime < 0.6) {
			this.rank = 'Rapid Reflexes...';
		} else {
			this.rank = 'Snail Pace... :(';
		}
	},
};
</script>

<style>
.rank {
	font-size: 1.4rem;
	color: #0faf87;
	font-weight: bold;
}
</style>
