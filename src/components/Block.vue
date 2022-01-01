<template>
	<div class="block" v-if="showBlock">click me</div>
</template>

<script>
export default {
	props: ['delay'],
	data() {
		return {
			showBlock: false,
		};
	},
	mounted() {
		setTimeout(() => {
			this.showBlock = true;
		}, this.delay);
		console.log('component mounted');
	},
	updated() {
		console.log('component update');
	},
	unmounted() {
		console.log('component unmounted');
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
</style>
