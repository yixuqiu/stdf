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

<div class="{size} m-auto relative flex items-center container">
	{#each [0, -0.125, -0.25, -0.375, -0.5, -0.625, -0.75, -0.875] as item, i}
		<div class="absolute left-0 right-0 flex" style="transform: rotate({i * 45}deg); animation-duration: {0.3 / speed}s">
			<div
				class="dot w-1.5 h-1.5 rounded-full{colorClass()}"
				style="background-color: {customColor[0]}; transform: translateX(12px); animation-duration: {0.9 /
					speed}s; animation-delay: calc({0.9 / speed}s * {item});"
			></div>
		</div>
	{/each}
</div>

<style>
	.container {
		animation: rotate linear infinite;
	}

	.dot {
		animation: oscillate ease-in-out infinite alternate;
	}

	@keyframes oscillate {
		0% {
			transform: translateX(12px) scale(0);
			opacity: 0.25;
		}

		100% {
			transform: translateX(0) scale(1);
			opacity: 1;
		}
	}

	@keyframes rotate {
		0% {
			transform: rotate(0deg);
		}
		100% {
			transform: rotate(360deg);
		}
	}
</style>
