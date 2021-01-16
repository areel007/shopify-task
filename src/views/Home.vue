<template>
	<div id="home">
		<warning-banner v-if="isNominationExceeded" />
		<Search @search-input="searchForInput($event)" @clear-search-input="clear($event)" />
		<div id="search-result-and-nominations">
			<div class="container">
				<div id="inner-result-and-nominations">
					<search-result @nominate="nominate($event)" :search-input="searchInput" :movies="movies"></search-result>
					<Nomination @remove-nomination="removeNomination($event)" :movies="nominatedMovies" />
				</div>
			</div>
		</div>
	</div>
</template>

<script>
	import env from '@/env.js'
	import axios from 'axios'
	import Search from "@/components/search/search";
	import SearchResult from "@/components/search-result/search-result";
	import Nomination from "@/components/nomination/nomination";
	import WarningBanner from "@/components/banner/warning-banner";

	export default {
		name: "Home",
		components: {WarningBanner, Nomination, SearchResult, Search},
		data () {
			return {
				searchInput: '',
				movies: [],
				nominatedMovies: [],
				isNominationExceeded: false,
			}
		},
		methods: {
			clear(event) {
				this.searchInput = event
			},
			async searchForInput(event) {
				this.searchInput = event
				const response = await axios.get(` http://www.omdbapi.com/?i=tt3896198&apikey=${env.apiKey}&s=${this.searchInput}`)
				if(response.data.Search === undefined ) {
					this.movies = []
					this.nominatedMovies = []
				} else {
					this.movies = response.data.Search
					this.nominatedMovies = []
					console.log(this.movies)
				}
			},
			nominate (event) {
				if(this.nominatedMovies.length < 5) {
					this.movies.forEach(movie => {
						if(movie.Title === event) {
							this.nominatedMovies.push(movie)
							this.isNominationExceeded = false
						}
					})
					this.movies = this.movies.filter(movie => movie.Title !== event)
				} else {
					this.isNominationExceeded = true
				}
			},
			removeNomination (e) {
				this.nominatedMovies = this.nominatedMovies.filter(movie => movie.Title !== e)
			}

		},
};
</script>

<style scoped>
	#home {
		width: 100%;
	}
	#search-result-and-nominations {
		width: 100%;
	}
	#inner-result-and-nominations {
		position: relative;
	}
</style>
