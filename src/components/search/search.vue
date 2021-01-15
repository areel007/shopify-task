<template>
	<div id="search">
		<div class="container">
			<div id="inner-search">
				<p id="search-header">Movie Information</p>
				<div id="search-box">
					<svg v-if="searchInput.trim().length=== 0" id="search-svg" viewBox="0 0 20 20" fill="none">
						<path id="search-svg-path" fill-rule="evenodd" clip-rule="evenodd" d="M8 16C3.58172 16 0 12.4183 0 8C0 3.58172 3.58172 0 8 0C12.4183 0 16 3.58172 16 8C16 9.84871 15.3729 11.551 14.3199 12.9056L19.7071 18.2929L18.2929 19.7071L12.9056 14.3199C11.551 15.3729 9.84871 16 8 16ZM14 8C14 11.3137 11.3137 14 8 14C4.68629 14 2 11.3137 2 8C2 4.68629 4.68629 2 8 2C11.3137 2 14 4.68629 14 8Z" fill="black"/>
					</svg>
					<svg @click="clearSearchInput" v-if="searchInput.trim().length>0" id="clear-svg" viewBox="0 0 24 24">
						<path d="M0 0h24v24H0z" fill="none"/><path d="M19 6.41L17.59 5 12 10.59 6.41 5 5 6.41 10.59 12 5 17.59 6.41 19 12 13.41 17.59 19 19 17.59 13.41 12z"/>
					</svg>
					<input @keyup="searchForInput" v-model="searchInput" type="text" placeholder="Search for movies...">
				</div>

			</div>
		</div>
	</div>
</template>

<script>
	export default {
		name: "search",
		data () {
			return {
				searchInput: ''
			}
		},
		methods: {
			clearSearchInput () {
				this.$emit('clear-search-input', '')
				this.searchInput = ''
			},
			searchForInput () {
				this.$emit('search-input', this.searchInput)
			}
		}
	}
</script>

<style scoped>
	#search {
		width: 100%;
		margin: 2em 0;
	}
	#inner-search {
		background-color: var(--tertiary-color);
		width: 100%;
		padding: 1em;
	}
	#search-header {
		font-weight: var(--font-weight-semibold);
		font-size: var(--font-size-15);
		letter-spacing: .1em;
		color: var(--primary-color);
		margin-bottom: 1em;
	}
	#search-box {
		margin: .5em 0;
		height: 40px;
		display: flex;
		align-items: center;
		width: 100%;
		background-color: var(--white);
		border-radius: 5px;
		/*border: 1px solid var(--secondary-color);*/
		padding: 0 .5em ;
	}
	#search-svg {
		width: 15px;
		height: 15px;
		margin-right: .5em;
	}
	#search-box input {
		width: 100%;
		border: none;
		outline: none;
		padding: .5em 0;
	}
	#search-svg-path {
		fill: var(--secondary-color);
	}
	#clear-svg {
		width: 20px;
		height: 20px;
		cursor: pointer;
		fill: red;
		margin-right: .5em;
	}

</style>