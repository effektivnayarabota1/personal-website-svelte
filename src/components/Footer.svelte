<script>
	let windowWidth;
</script>

<svelte:window bind:innerWidth={windowWidth} />

<footer class="grid mono">
	<nav class="main">
		<a href="#">Галлерея</a>
		<a href="#">Связь</a>
	</nav>
	<nav class="social">
		<span>
			<a href="">Telegram</a>
			<a href="">Gmail</a>
			<a href="">Instagram</a>
			<a href="">TgChanel</a>
			{#if windowWidth >= 1920}
				<a href="">SoundCloud:</a>
				<div class="sc">
					<a href="">Плейлист культа Богини Цветов</a>
					<span>
						<a href="">0</a>
						<a href="">.33</a>
						<a href="">.67</a>
						<a href="">.777</a>
						<a href="">1</a>
					</span>
				</div>
			{:else if windowWidth >= 1280}
				<a href="">SoundCloud</a>
				<a href="">Плейлист культа Богини Цветов</a>
			{:else}
				<a href="">SoundCloud</a>
			{/if}
		</span>
	</nav>
	<nav class="promo">
		<a href="">
			Телеграм-бот для Notion – <br />
			Текстовые, голосовые и фото заметки в ноушн через телегу!
		</a>
		<a href="">
			ПУТЬ К ХРАМУ БОГИНИ ЦВЕТОВ – <br />
			... Ее взгляд также был очень разным. Зависел толи он угла зрения, толи
			от ее расположения духа. От теплого, невероятно нежного и успокаивающего,
			до холодного, прорезающего на сквозь и бросающего в жар...
		</a>
	</nav>
	<nav class="info">
		<p>EFFECTIVNAYARABOTA1!</p>
		<p>2022 Novosibirsk © All rights reserved</p>
	</nav>
</footer>

<style>
	/* TODO Ограничить ширину футера в 1920px */
	footer {
		padding-top: 80px;
		padding-bottom: 96px;

		background-image: url(./footer/clouds.jpg);
		background-size: cover;
		background-position: center;
	}
	nav {
		height: min-content;
		display: flex;
		flex-direction: column;
		align-content: flex-start;
		gap: 16px;
	}
	span {
		display: flex;
		flex-wrap: wrap;
		gap: 16px;
	}
	.sc {
		display: flex;
		flex-direction: column;
		padding-left: 16px;
	}
	.info {
		align-items: flex-end;
	}
	@media (max-width: 1919px) {
		.grid {
			grid-template-areas:
				"main social promo"
				". info promo"
				". . promo";
		}
		nav {
			flex-wrap: wrap;
		}
		.main {
			/* grid-area: main; */
			flex-direction: row;
			grid-column: 1 / 2;
			grid-row: 1 / 2;
		}
		.social {
			grid-area: social;
		}
		.promo {
			grid-area: promo;
		}
		.info {
			grid-area: info;
			align-self: start;
			/* flex-direction: row; */
			align-items: flex-start;
		}
	}

	@media (max-width: 1715px) {
		footer {
			padding-top: 64px;
			padding-bottom: 64px;
		}
		.grid {
			grid-template-areas:
				"main promo"
				"social promo"
				"info promo"
				". promo";
		}
		.info {
			margin-top: 16px;
		}
	}
	@media (max-width: 1287px) {
		.grid {
			grid-template-areas:
				"main promo promo"
				"social promo promo"
				"info promo promo"
				". promo promo";
		}
	}
	@media (max-width: 1023px) {
		.grid {
			grid-template-areas:
				"main promo promo"
				"social promo promo"
				"social info info";
		}
		.info {
			flex-direction: row;
		}
	}
	@media (max-width: 767px) {
		.grid {
			grid-template-areas:
				"main"
				"social"
				"promo"
				"info";
		}
		.info {
			flex-direction: row;
		}
	}
</style>
