<template>
	<div id="app">
		<Header />
		<router-view />
	</div>
</template>

<style>

</style>
<script>
	import Header from "@/components/header/header";
	export default {
		components: {Header}
	}
</script>

<style>
	@import "./style/guide.css";

	* {
		margin: 0;
		padding: 0;
		box-sizing: border-box;
	}
	.container {
		width: 90%;
		max-width: 1440px;
		margin: 0 auto;
	}
	#app {
		font-family: var(--roboto);
	}
</style>