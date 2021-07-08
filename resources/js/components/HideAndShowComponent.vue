<template>
	<span>
		<div v-if="is_show">
			Show Me - I'm Here
		</div>
		<div>
			<button @click="showUp">Show</button>
			<button @click="hideUp">Hide</button>
		</div>
	</span>
</template>
<script>
	export default {
		data() {
			return {
				is_show: false,
			}
		},
		methods: {
			showUp() {
				this.is_show = true
			},

			hideUp() {
				this.is_show = false
			},
		},
	}
</script>