<script>
	import Card from "./Home_gallery_card.svelte";
</script>

<section>
	<Card />
	<Card />
	<Card />
	<Card />
	<Card />
	<Card />
	<Card />
</section>

<style>
	section {
		/* width: 100%; */
		min-height: 100vh;
		padding: 320px 24px;

		display: grid;
		justify-content: center;

		/* TODO При увеличении количества проектов сделай сетку на 5 или 7 колонок. */
		grid-template-columns: repeat(3, 400px);
		grid-gap: 12px;
	}
	@media (max-width: 1365px) {
		section {
			grid-template-columns: repeat(3, minmax(30%, 400px));
		}
	}
	@media (max-width: 1079px) {
		section {
			padding: 320px 16px;
			grid-template-columns: repeat(2, minmax(30%, 400px));
		}
	}
	@media (max-width: 600px) {
		section {
			padding: 320px 12px;
			grid-template-columns: repeat(1, minmax(30%, 400px));
		}
	}
</style>
