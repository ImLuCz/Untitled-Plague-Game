<template>
	<title>Untitled Plague Game - Homepage</title>

	<!-- Particles -->
	<div>
		<div class="rain front-row">
			<div v-for="(drop, index) in drops" :key="index" v-html="drop"></div>
		</div>
		<div class="rain back-row">
			<div v-for="(backDrop, index) in backDrops" :key="index" v-html="backDrop"></div>
		</div>
	</div>
</template>

<script>
export default {
	mounted() {
		this.makeItRain();
	},
	data() {
		return {
			drops: [],
			backDrops: []
		};
	},
	methods: {
		makeItRain() {
			let increment = 0;

			while (increment < 100) {
				const randoHundo = Math.floor(Math.random() * (98 - 1 + 1) + 1);
				const randoFiver = Math.floor(Math.random() * (5 - 2 + 1) + 2);
				increment += randoFiver;

				const drop = `
					<div class="drop" style="left: ${increment}%; bottom: ${randoFiver + randoFiver - 1 + 90}%; animation-delay: 0.${randoHundo}s; animation-duration: 0.5${randoHundo}s;">
						<div class="stem" style="animation-delay: 0.${randoHundo}s; animation-duration: 0.5${randoHundo}s;"></div>
						<div class="splat" style="animation-delay: 0.${randoHundo}s; animation-duration: 0.5${randoHundo}s;"></div>
					</div>
				`;
				const backDrop = `
					<div class="drop" style="right: ${increment}%; bottom: ${randoFiver + randoFiver - 1 + 90}%; animation-delay: 0.${randoHundo}s; animation-duration: 0.5${randoHundo}s;">
						<div class="stem" style="animation-delay: 0.${randoHundo}s; animation-duration: 0.5${randoHundo}s;"></div>
						<div class="splat" style="animation-delay: 0.${randoHundo}s; animation-duration: 0.5${randoHundo}s;"></div>
					</div>
				`;

				this.drops.push(drop);
				this.backDrops.push(backDrop);
			}
		},
	}
};
</script>

<style lang="scss">

</style>