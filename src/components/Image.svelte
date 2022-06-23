<script>
	import Text from "./Image_text.svelte";
</script>

<section class="grid">
	<figure class="image">
		<picture>
			<img src="vertical.jpg" alt="" />
		</picture>
		<figcaption>
			<Text />
		</figcaption>
	</figure>
</section>
<section class="grid">
	<figure class="image">
		<picture>
			<img src="horizontal.jpg" alt="" />
		</picture>
		<figcaption>
			<Text />
		</figcaption>
	</figure>
</section>
<section class="grid">
	<figure class="image">
		<picture>
			<img src="square.jpg" alt="" />
		</picture>
		<figcaption>
			<Text />
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
