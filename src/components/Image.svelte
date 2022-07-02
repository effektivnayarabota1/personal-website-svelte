<script>
	import { onMount } from "svelte/internal";
	import Text from "./Image_text.svelte";

	let innerWidth;
	let innerHeight;
	let vertical = false;
	let indicator = true;

	let grid;
	let gap;
	let padding;

	let columns;

	// $: if (grid) {
	// 	gap = parseInt(getComputedStyle(grid).columnGap, 10);
	// 	padding = parseInt(getComputedStyle(grid).paddingTop, 10);
	// }

	let img;
	let img_width;
	let img_height;

	onMount(() => {
		img_width = img.width;
		img_height = img.height;
		gap = parseInt(getComputedStyle(grid).columnGap, 10);
		padding = parseInt(getComputedStyle(grid).paddingTop, 10);
		if (gap + padding * 2 + img_width < outerWidth - 600) {
			vertical = true;
			if (img_width > 1080) {
				// TODO Если изображине больше суммы 2й и 3й колонки, тогда оно начинает занимать четверную колонку.
				columns = getComputedStyle(grid)
					.gridTemplateColumns.split(" ")
					.map((column) => {
						return parseInt(column, 10);
					});
				let colSum = columns[1] + columns[2] + gap;
				console.log(colSum);
				if (colSum < img_width) {
					console.log("fullSize");
					// TODO Настроить figure container под grid, а не flexbox;
					// TODO Если изображине больше суммы 2й, 3й и 4й колонки, тогда оно начинает занимать все колонки.
				}
			} else if (img_height + padding + 80 < innerHeight) {
				indicator = false;
				// TODO Пробрасываю индикатор на текстовый компонент.
			}
		}
	});
</script>

<svelte:window bind:innerWidth bind:innerHeight />

<section class="grid" bind:this={grid}>
	<figure class:vertical class="image">
		<picture>
			<img bind:this={img} src="horizontal.jpg" alt="" />
			<!-- on:load={handleImageLoad} -->
		</picture>
		<figcaption>
			<Text {vertical} {indicator} />
		</figcaption>
	</figure>
</section>

<style>
	figure {
		width: 100%;
		display: flex;
		flex-direction: row;
		justify-content: flex-end;
		gap: var(--gap);
		grid-column: 2 / 5;
	}
	picture {
		max-height: 100vh;
		max-width: 100%;
		padding: var(--padding) 0;
		/* align-self: flex-end; */
	}
	img {
		max-width: 100%;
		max-height: 100%;
	}
	figcaption {
		padding: calc(var(--padding) + 8px) 8px 0;
		min-width: 600px;
		width: 600px;
	}
	@media (max-width: 1919px) {
		figure {
			grid-column: 1/4;
		}
		.vertical > figcaption {
			padding: calc(var(--padding) + 8px) 8px 0;
		}
	}
	@media (max-width: 1715px) {
		/* TODO Не получается сделать перебрасыание текстового блока без JS */
		figure {
			grid-column: 1/3;
			flex-wrap: wrap;
			justify-content: flex-start;
			align-content: flex-start;
			gap: 0;
		}
		.vertical {
			flex-wrap: nowrap;
			gap: var(--gap);
		}
		picture {
			padding: var(--padding) 0 0;
			max-height: calc(100vh - var(--padding));
		}
		figcaption {
			padding: 0 8px 0;
			min-width: auto;
			max-width: 600px;
		}
	}
	@media (max-width: 1287px) {
		figure {
			grid-column: 1/4;
		}
	}
	@media (max-width: 1023px) {
	}
	@media (max-width: 767px) {
		figcaption {
			width: 100%;
		}
	}
</style>
