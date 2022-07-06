<script>
	export let vertical;
	export let indicator;
</script>

<div class:vertical class:indicator>
	<img src="navigation/text-indicator.svg" alt="unread text indicator" />
</div>
<h1>Форма и Цвет храма.</h1>
<p>
	Храм был высечен из цельного куска белой мраморной скалы с вкраплениями жил
	большого количества разных пород. Уникальные сочетания материалов добавляли
	храму природного величия. Тщательная полировка заставляла блестеть эти
	минералы и руды. Много путников пало, пытаясь ощутить могущество этого
	вечного здания. Было очевидно, что создать красоту такого масштаба без
	помощи божества простым архитекторам было просто невозможно.
</p>
<p class="desc">105x75, акрил, холст лен</p>

<style>
	div {
		display: none;
	}
	.indicator {
		width: 64px;
		height: 80px;
		padding-top: 6px;

		display: flex;
		align-items: center;
		flex-direction: column;
	}
	h1 {
		margin-bottom: 24px;
	}
	p {
		margin-bottom: 16px;
	}
	@media (max-width: 767px) {
		.indicator {
			width: 36px;
			height: 48px;
			padding: 2px;
		}
		.indicator img {
			height: 6px;
		}
	}
</style>
