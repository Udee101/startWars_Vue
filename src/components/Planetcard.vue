<template>
	<div class="planet-container" v-for="(planet, i) in planets" :key="i">
		<div class="planet-image">
			<img :src="require(`@/assets/images/${planet.name}.jpg`)" alt="images" />
		</div>
		<div class="planet-details">
			<h3>Name: {{ planet.name }}</h3>
			<p>Climate: {{ planet.climate }}</p>
			<p>Surface-Water: {{ planet.surface_water }}</p>
		</div>
	</div>
</template>

<script>
	export default {
		name: "PlanetCard",
		props: ["planets"],
	};
</script>

<style scoped>
	.planet-container {
		width: 250px;
		height: 400px;
		margin: 10px;
		padding: 10px;
		background: whitesmoke;
		border-radius: 5px;
		box-sizing: border-box;
	}
	.planet-container:hover {
		cursor: pointer;
	}
	.planet-image {
		width: 100%;
		height: 60%;
		margin-bottom: 5px;
	}
	img {
		width: 100%;
		height: 100%;
		border-radius: 5px;
	}
	.planet-details {
		width: 100%;
		height: 40%;
		margin-top: 10px;
		display: block;
	}
	.planet-details h3 {
		font-size: 16px;
		font-weight: bold;
	}
</style>