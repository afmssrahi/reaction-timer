<template>
	<div class="block">click me</div>
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
		console.log('component mounted');
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
