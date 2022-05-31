<template>
	<header>
		<PageHead />
	</header>
	<FetchedPlanets />
</template>

<script>
	import FetchedPlanets from "./components/FetchPlanets.vue";
	import PageHead from "./components/PageHead.vue";

	export default {
		name: "App",
		components: {
			PageHead,
			FetchedPlanets,
		},
	};
</script>

<style scoped>
	#app {
		font-family: Avenir, Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		text-align: center;
		margin-top: 60px;
		padding: 10px;
	}
</style>
