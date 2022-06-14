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
		width: 100%;
		min-height: 100vh;

		padding: 320px 20%;

		display: grid;
		justify-content: center;
		align-content: center;

		/* grid-template-columns: repeat(3, 320px); */
		grid-template-columns: repeat(3, 400px);
		grid-gap: 12px;
	}
	/* @media (max-width: 1280px) { */
	/* 	section { */
	/* 		padding: 120px 5%; */
	/* 		grid-template-columns: repeat(3, 1fr); */
	/* 		grid-gap: 2%/3.36%; */
	/* 	} */
	/* } */
	@media (max-width: 1280px) {
		section {
			padding: 80px 5%;
			grid-template-columns: repeat(2, 1fr);
		}
	}
	@media (max-width: 600px) {
		section {
			padding: 240px 4%;
			grid-template-columns: repeat(1, 1fr);
			grid-gap: 16px;
		}
	}
</style>
