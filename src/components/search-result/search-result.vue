<template>
	<div id="search-result" :class="{ser: !movies.length>0}">
		<p v-if="searchInput" id="search-result-title-one">Search result for "{{ searchInput }}"</p>
		<p v-else id="search-result-title-two">The search input is empty</p>
		<ul>
			<li v-for="(movie, index) in movies" :key="index">
				{{ movie.Title }} <span id="date">({{ movie.Year }})</span>
				<button  @click="$emit('nominate', movie.Title)">Nominate</button>
			</li>
		</ul>
	</div>
</template>

<script>
	export default {
		name: "search-result",
		props: {
			searchInput: {
				type: String,
				required: true,
			},
			movies: {
				type: Array,
				required: true,
			},
		},
	}
</script>

<style scoped>
	.ser {
		background-color: transparent !important;
	}
	#search-result {
		padding: 1em;
		background-color: var(--tertiary-color);
		width: 49%;
	}
	#search-result-title-one, #search-result-title-two {
		color: var(--secondary-color);
		font-weight: var(--font-weight-semibold);
		font-size: var(--font-size-14);
	}
	#search-result ul {
		margin: 1em 0;
	}
	#search-result ul li {
		margin-bottom: .5em;
		padding: 1em;
		font-size: var(--font-size-14);
		color: var(--secondary-color);
		list-style: none;
		background-color: var(--white);
		border-radius: 5px;
		cursor: pointer;
		transition: all .1s ease-in-out;
		width: 100%;
	}
	#search-result ul li:hover {
		transform: scaleX(1.02);
	}
	button {
		padding: .4em 1em;
		cursor: pointer;
		margin-left: 1em;
		font-size: var(--font-size-12);
		background-color: var(--primary-color);
		border: none;
		color: var(--white);
		outline: none;
		border-radius: 4px;
	}
	#date {
		font-weight: var(--font-weight-semibold);
		font-style: italic;
	}

	@media screen and (max-width: 1100px){
		#search-result {
			width: 100%;
		}
	}

	@media screen and (max-width: 450px){
		#search-result ul li {
			line-height: 2;
		}
	}


</style>