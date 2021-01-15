<template>
	<header>
		<div class="container">
			<div id="inner-header">
				<div id="logo">
					<img src="../../assets/shopify-logo.png" >
				</div>
				<p id="logo-title">The Shoppies</p>
			</div>
		</div>
	</header>
</template>

<script>
	export default {
		name: "page-header"
	}
</script>

<style scoped>
	header {
		width: 100%;
		background-color: var(--primary-color);
		font-family: var(--roboto);
		z-index: 20;
	}
	#inner-header {
		width: 100%;
		display: flex;
		align-items: center;
		padding: .5em 0;
	}
	#logo {
		margin-right: .5em;
		width: 40px;
	}
	#logo img {
		width: 100%;
	}
	#logo-title {
		color: var(--white);
		font-size: var(--font-size-20);
		font-weight: var(--font-weight-semibold);
	}

	@media screen and (max-width: 800px){
		header {
			position: sticky;
			top: 0;
		}
	}

</style>