<script>
	import cover from "/home/card/glass.jpg";
</script>

<div class="card">
	<div class="card_hover">
		<div class="card_text  mono">
			<a href="#" class="difference"
				>Redesign personal website/portfolio</a
			>
			<p class="difference">
				<!-- TODO Ограничить количество строк -->
				Сайт разрабатываю для художника (себя), поэтому бОльшая часть внимания
				пользователя должна быть посвящена изображениям.
			</p>
		</div>
		<div class="card_highlight">
			<div class="line1" />
			<div class="line2" />
		</div>
		<img class="card_texture" src={cover} alt="Текстура для анимации." />
		<div class="card_white" />
	</div>
</div>

<style>
	.card {
		aspect-ratio: 400/240;
		/* width: 100%;
		height: 100%; */

		border-radius: 8px;
		overflow: hidden;

		/* width: 360px;
		height: 240px;
		overflow: hidden; */

		background-image: url(./home/card/cover.jpg);
		background-size: cover;
		background-position: center;

		/* Почему-то фильтр подрезает все изображение... */
		filter: drop-shadow(0 4px 2px rgba(0, 0, 0, 0.4));
		/* box-shadow: 12px 12px 2px 1px rgba(0, 0, 255, 0.2); */
	}

	.card_hover {
		width: 100%;
		height: 100%;
	}
	.card_hover > * {
		width: 100%;
		height: 100%;
		position: absolute;
	}

	.card_text {
		z-index: 2;

		width: 100%;
		height: 100%;
		padding: 12px 16px;

		display: flex;
		flex-direction: column;
		justify-content: flex-end;
	}
	.card_text > p {
		padding-top: 16px;
	}

	.card_highlight {
		z-index: 1;
		mix-blend-mode: soft-light;
	}
	.card_highlight > * {
		position: absolute;
		transform: rotate(30deg);
		filter: blur(4px);

		background: linear-gradient(
			172.78deg,
			rgba(255, 255, 255, 0.8) 24.11%,
			rgba(255, 255, 255, 0) 81.68%
		);
	}
	.line1 {
		width: 8%;
		height: 200%;

		left: 36%;
		top: -80%;
	}
	.line2 {
		width: 32%;
		height: 200%;

		left: 54%;
		top: -80%;
	}
	.card_texture {
		mix-blend-mode: luminosity;
		backdrop-filter: blur(4px);
	}
	.card_white {
		background-color: white;
		opacity: 64%;
	}

	@media (max-width: 1280px) {
		.card {
			border-radius: 2.5%/4.2%;
		}
	}
</style>
