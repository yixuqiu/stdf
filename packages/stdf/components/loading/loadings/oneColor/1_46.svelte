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

<div class="{size} m-auto flex flex-col justify-center">
	<div class="relative flex items-center justify-between w-full h-1/5 -translate-x-[10%]">
		{#each [0, -0.2, -0.4, -0.6, -0.8] as item}
			<div
				class="dot absolute w-1/5 h-full rounded-full{colorClass()}"
				style="background-color: {customColor[0]};animation-delay: {(2.5 / speed) * item}s;animation-duration: {2.5 / speed}s"
			></div>
		{/each}
	</div>
</div>

<style>
	.dot {
		animation: stream linear infinite both;
	}

	@keyframes stream {
		0%,
		100% {
			transform: translateX(0) scale(0);
		}

		50% {
			transform: translateX(16px) scale(1);
		}

		99.999% {
			transform: translateX(32px) scale(0);
		}
	}
</style>
