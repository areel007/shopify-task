<template>
	<div id="nomination" :class="{nom: !movies.length>0}">
		<p id="search-result-title-one">Nominations</p>
		<ul>
			<li v-for="(movie, index) in movies" :key="index">
				{{ movie.Title }} <span id="date">({{ movie.Year }})</span>
				<button @click="$emit('remove-nomination')">Remove</button>
			</li>
		</ul>
		<p id="share-header" @click="show">Share</p>
		<Share v-show="isShown" />
	</div>
</template>

<script>
	import Share from "@/components/share/share";
	export default {
		name: "nomination",
		components: {Share},
		props: {
			movies: {
				type: Array,
				required: true,
			}
		},
		data () {
			return {
				isShown: false
			}
		},
		methods: {
			show () {
				this.isShown = !this.isShown
			}
		}
	}
</script>

<style scoped>
	.nom {
		display: none !important;
	}
	#nomination {
		padding: 1em;
		background-color: var(--tertiary-color);
		width: 49%;
		position: absolute;
		right: 0;
		top: 0;
	}
	#nomination p {
		color: var(--secondary-color);
		font-weight: var(--font-weight-semibold);
	}
	#nomination ul {
		margin: 1em 0;
	}
	#nomination ul li {
		margin-bottom: .5em;
		padding: 1em;
		font-size: var(--font-size-14);
		color: var(--secondary-color);
		list-style: none;
		background-color: var(--white);
		white-space: nowrap;
		border-radius: 5px;
		cursor: pointer;
		transition: all .1s ease-in-out;
	}
	#nomination ul li:hover {
		transform: scaleX(1.02);
	}
	button {
		padding: .4em 1em;
		cursor: pointer;
		margin-left: .5em;
		font-size: var(--font-size-12);
		background-color: var(--red);
		border: none;
		color: var(--white);
		outline: none;
		border-radius: 4px;
	}
	#date {
		font-weight: var(--font-weight-semibold);
		font-style: italic;
	}
	#share-header {
		font-size: var(--font-size-14);
		cursor: pointer;
		width: min-content;
		color: var(--primary-color) !important;
		font-weight: var(--font-weight-semibold) !important;
		margin-bottom: .5em;
	}

	@media screen and (max-width: 1100px){
		#nomination {
			position: relative;
			width: 100%;
		}
	}

</style>