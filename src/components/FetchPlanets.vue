<template>
	<main>
		<div class="cards_layout">
			<PlanetCard :planets="planets" />
		</div>
		<div class="pagination">
			<VueTailwindPagination
				:current="currentPage"
				:total="total"
				:per-page="perPage"
				@page-changed="pageChange($event)"
			/>
		</div>
	</main>
</template>

<script>
	import "@ocrv/vue-tailwind-pagination/styles";
	import VueTailwindPagination from "@ocrv/vue-tailwind-pagination";
	import axios from "axios";
	import PlanetCard from "./Planetcard.vue";
	// import PageButtons from "./PageButtons.vue";
	export default {
		name: "FetchedPlanets",
		components: {
			PlanetCard,
			VueTailwindPagination,
		},
		mounted() {
			this.currentPage = 1;
			this.getPlanets();
		},
		data() {
			return {
				currentPage: 0,
				total: 0,
				perPage: 0,
				planets: [],
			};
		},
		methods: {
			getPlanets() {
				axios
					.get(`https://swapi.dev/api/planets/?page=${this.currentPage}`)
					.then((res) => {
						this.planets = res.data.results;
						this.total = res.data.count / 2;
						this.perPage = res.data.results.length;
						console.log(res.data);
					})
					.catch((error) => {
						console.log(error);
					});
			},
			pageChange(pageNumber) {
				this.currentPage = pageNumber;
				this.getPlanets();
			},
		},
	};
</script>

<style scoped>
	main {
		display: block;
		padding: 15px;
		background: linear-gradient(
			to bottom,
			rgb(255, 255, 255),
			rgb(49, 49, 116),
			rgba(118, 208, 247, 0.5)
		);
	}
	.cards_layout {
		font-family: Avenir, Helvetica, Arial, sans-serif;
		display: flex;
		justify-content: center;
		flex-wrap: wrap;
	}
	.pagination {
		display: flex;
		justify-content: center;
		width: 100%;
		height: 50px;
		margin-bottom: 20px;
		box-sizing: border-box;
	}
</style>