<script>
	import { onMount } from "svelte/internal";
	import Text from "./Image_text.svelte";
	//
	let innerWidth;
	let innerHeight;

	let grid;
	let picture;
	let gap;
	let padding;
	let columns;

	let vertical = false;
	let indicator = false;
	let fullSize = false;

	let img;
	let img_width;
	let img_height;
	let img_natWidth;
	let img_natHeight;

	onMount(() => {
		img_width = img.width;
		img_height = img.height;

		img_natWidth = img.naturalWidth;
		img_natHeight = img.naturalHeight;

		gap = parseInt(getComputedStyle(grid).columnGap, 10);
		padding = parseInt(getComputedStyle(picture).paddingTop, 10);

		columns = getComputedStyle(grid)
			.gridTemplateColumns.split(" ")
			.map((column) => {
				return parseInt(column, 10);
			});
		let colSum = columns[1] + columns[2] + gap;

		// TODO Сделать изображение на фуллсайз.
		// Необходимо, чтобы оно выходило за рамки текущего блока и центровалось.
		// fullSize detection
		// if (img_natWidth > colSum) {
		// 	console.log("fullSize3");
		// 	fullSize = "fullSize3";
		//
		// 	colSum = colSum + columns[3] + gap;
		// 	if (img_natWidth > colSum) {
		// 		console.log("fullSize4");
		// 		fullSize = "fullSize4";
		// 	}
		// }

		if (!fullSize) {
			if (gap + padding * 2 + img_width < innerWidth - 600) {
				// vertical detection

				console.log("vertical");
				vertical = true;
			} else {
				// indicator detection

				if (img_height + padding >= innerHeight - padding) {
					console.log("indicator");
					indicator = true;
				}
			}
		}
	});
</script>

<svelte:window bind:innerWidth bind:innerHeight />

<figure class:vertical class:indicator class="grid image" bind:this={grid}>
	<picture bind:this={picture}>
		<img bind:this={img} src="horizontal.jpg" alt="" />
	</picture>
	<figcaption>
		<Text {vertical} {indicator} {fullSize} />
	</figcaption>
</figure>

<style>
	/* настройка фуллсайза */
	/* @media (min-width: 1920px) { */
	/* 	figure.fullSize3 { */
	/* 		grid-template-areas: */
	/* 			". img img img" */
	/* 			". . text ."; */
	/* 	} */
	/* 	.fullSize3 img { */
	/* 		float: left; */
	/* 	} */
	/* 	figure.fullSize4 { */
	/* 		grid-template-areas: */
	/* 			"img img img img" */
	/* 			". . text ."; */
	/* 	} */
	/* } */

	figure {
		width: 100%;
		margin: auto;

		gap: var(--gap);
		grid-template-areas: ". img img text";
	}
	figure.indicator {
		gap: 0;
	}
	picture {
		max-height: 100vh;
		max-width: 100%;
		padding: calc(var(--padding) - 8px) 0;
		/* padding: calc(var(--padding)) 0;*/

		grid-area: img;
	}
	.indicator picture {
		padding-bottom: 0;
		max-height: calc(100vh - var(--padding));
	}
	img {
		float: right;
		max-width: 100%;
		max-height: 100%;
	}
	figcaption {
		min-width: 600px;
		width: 600px;
		margin: var(--padding) 0 0;
		padding: 8px;

		grid-area: text;
	}
	@media (max-width: 1919px) {
		figure {
			grid-template-areas: "img img text";
		}
	}
	@media (max-width: 1715px) {
		figure {
			grid-template-areas:
				"img img"
				"text .";
		}
		img {
			float: left;
		}
		figcaption {
			min-width: auto;
			max-width: 600px;
			margin: 0;
			padding-top: 0;
		}

		.vertical {
			grid-template-areas: "img text";
			gap: var(--gap);
		}
		.vertical picture {
			max-height: 100vh;
			padding: var(--padding) 0;
		}
		.vertical img {
			float: right;
		}
		.vertical figcaption {
			margin: var(--padding) 0 0;
		}
	}
	@media (max-width: 1287px) {
		figure {
			grid-template-areas:
				"img img img"
				"text text text";
		}

		.vertical {
			grid-template-areas: "img text text";
			gap: var(--gap);
		}
	}
	@media (max-width: 1023px) {
	}
	@media (max-width: 767px) {
		figcaption {
			width: 100%;
		}
		picture {
			padding: var(--padding) 0;
		}

		.vertical {
			grid-template-areas:
				"img img img"
				"text text text";
			gap: var(--gap);
		}
	}
	/*TODO Пробегись по высотам экрана, кажется что достаточно просто убавить паддинги, все выглядит достаточно красиво.*/
</style>
