<template>
	<div id="warning-banner">
		<div class="container">
			<div id="inner-banner">
				<p id="warning-message">You can only nominate five (5) movies</p>
			</div>
		</div>
	</div>
</template>

<script>
	export default {
		name: "warning-banner",
	}
</script>

<style scoped>
	#warning-banner {
		width: 100%;
		background-color: var(--secondary-color);
		position: sticky;
		top: 0px;
	}
	#inner-banner {
		display: flex;
		align-items: center;
		justify-content: center;
		width: 100%;
		height: 50px;
		position: relative;
	}
	#warning-message {
		color: var(--white);
	}

</style>