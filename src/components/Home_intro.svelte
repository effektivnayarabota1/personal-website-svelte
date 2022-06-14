<script>
	import letter from "/home/intro/letter.svg";

	let squares = [];
	for (let i = 1; i <= 24; i++) {
		squares.push(i);
	}
</script>

<section>
	{#each squares as square}
		<div>
			<img src={letter} alt="Вступительная анимация, буква." />
		</div>
	{/each}
</section>

<style>
	/*TODO Сделать гибкую верстку по вертикали тоже.*/

	section {
		width: 100%;
		height: 100vh;
		overflow: hidden;

		padding: 12%;

		background-image: url(./home/intro/flowers.jpg);
		background-size: cover;
		background-position: center;

		display: grid;
		justify-content: center;
		align-content: center;
		align-items: center;

		grid-template-columns: repeat(24, 1fr);
	}
	div {
		margin: 0 -16% 0;
	}
	img {
		vertical-align: top;
		mix-blend-mode: difference;
	}
	@media (min-width: 1920px) {
		section {
			grid-template-columns: repeat(24, 64px);
		}
	}
	@media (max-width: 1024px) {
		section {
			grid-template-columns: repeat(8, 1fr);
		}
		img {
			margin: 4% 0;
		}
	}
	@media (max-width: 820px) {
		section {
			grid-template-columns: repeat(6, 1fr);
		}
	}
	@media (max-width: 600px) {
		section {
			padding: 0;
			grid-template-columns: repeat(4, minmax(auto, 16%));
			grid-template-rows: repeat(6, minmax(1fr, 8%));
		}
		img {
			height: 100%;
		}
	}
</style>
