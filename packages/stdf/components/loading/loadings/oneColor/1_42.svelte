<script>
	export let theme = false;
	export let inverse = false;
	export let size = 'w-8 h-8';
	export let customColor = [];
	export let speed = 1;

	const colorClass = () => {
		if (inverse) {
			return theme ? ' bg-dark dark:bg-primary' : ' bg-white dark:bg-black';
		} else {
			return theme ? ' bg-primary dark:bg-dark' : ' bg-black dark:bg-white';
		}
	};
</script>

<div class="{size} m-auto relative inline-block container" style="animation-duration: {1.5 / speed}s;">
	{#each [120, -120, 0] as item}
		<div class="absolute h-full" style="transform: rotate({item}deg);left: 37.5%;width:25%;">
			<div
				class="dot absolute top-0 left-0 h-0 w-full rounded-full{colorClass()}"
				style="background-color: {customColor[0]};padding-bottom: 100%;animation-duration: {1.5 / speed}s;"
			></div>
		</div>
	{/each}
</div>

<style>
	.container {
		animation: spin infinite linear;
	}
	.dot {
		animation: wobble infinite ease-in-out;
	}

	@keyframes spin {
		0% {
			transform: rotate(0deg);
		}
		100% {
			transform: rotate(360deg);
		}
	}

	@keyframes wobble {
		0%,
		100% {
			transform: translateY(0%);
		}
		50% {
			transform: translateY(65%);
		}
	}
</style>
