<template>
	<div id="share">
		<p id="share-link-header">Share a link to this nomination(s)</p>
		<div id="nomination-input-box">
			<input type="text" :value="'http://localhost' + $route.path">
		</div>
	</div>
</template>

<script>
	export default {
		name: "share"
	}
</script>

<style scoped>
	#share {
		width: 60%;
		background-color: var(--white);
		padding: 1em;
		border-radius: 5px;
	}
	#share-link-header {
		font-size: var(--font-size-14);
		margin-bottom: .5em;
		font-style: italic;
		color: var(--secondary-color);
	}
	#nomination-input-box {
		width: 100%;
		padding: .5em;
		border: 1px solid var(--smoke-white);
		border-radius: 4px;
	}
	#nomination-input-box input {
		width: 100%;
		border: none;
		outline: none;
		font-size: var(--font-size-16);
		color: var(--primary-color);
	}

	@media screen and (max-width: 1100px){
		#share {
			position: relative;
			width: 100%;
		}
	}

</style>