<template>
	<span>
		<div>
			Butang yang telah di tekan: {{ number }}
		</div>
		<div>
			<button @click="countUp">Click Me</button>
		</div>
	</span>
</template>

<script>
	export default {
		data() {
			return {
				number: 0,
			}
		},
		methods: {
			countUp() {
				this.number++
			},
		},
	}
</script>

<style>
	
</style>