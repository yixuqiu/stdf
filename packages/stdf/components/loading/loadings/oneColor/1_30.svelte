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

<div class="{size} m-auto flex justify-between items-end">
	{#each [0, -0.36, -0.2] as item}
		<div class="cube w-2 h-2" style="animation-duration: {1.75 / speed}s; animation-delay: calc({1.75 / speed}s * {item})">
			<div
				class="cube__inner w-2 h-2 rounded-sm{colorClass()}"
				style="background-color: {customColor[0]}; animation-duration: {1.75 / speed}s; animation-delay: calc({1.75 / speed}s * {item})"
			></div>
		</div>
	{/each}
</div>

<style>
	.cube {
		animation: jump ease-in-out infinite;
	}

	.cube__inner {
		animation: morph ease-in-out infinite;
	}

	@keyframes jump {
		0% {
			transform: translateY(0px);
		}

		30% {
			transform: translateY(0px);
			animation-timing-function: ease-out;
		}

		50% {
			transform: translateY(-200%);
			animation-timing-function: ease-in;
		}

		75% {
			transform: translateY(0px);
			animation-timing-function: ease-in;
		}
	}

	@keyframes morph {
		0% {
			transform: scaleY(1);
		}

		10% {
			transform: scaleY(1);
		}

		20%,
		25% {
			transform: scaleY(0.8) scaleX(1.3);
			animation-timing-function: ease-in-out;
		}

		30% {
			transform: scaleY(1.15) scaleX(0.9);
			animation-timing-function: ease-in-out;
		}

		40% {
			transform: scaleY(1);
		}

		70%,
		85%,
		100% {
			transform: scaleY(1);
		}

		75% {
			transform: scaleY(0.8) scaleX(1.2);
		}
	}
</style>
