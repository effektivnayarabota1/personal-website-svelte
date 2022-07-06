<script>
	import TextBlock from "./Text_block.svelte";
</script>

<section class="grid">
	<article>
		<TextBlock />
	</article>
</section>

<style>
	article {
		grid-column: 3/4;
		margin-bottom: 240px;
	}
	@media (max-width: 1919px) {
		article {
			grid-column: 2/3;
		}
	}
	@media (max-width: 1715px) {
		article {
			grid-column: 1/3;
			width: 620px;
			justify-self: center;
		}
	}
	@media (max-width: 1287px) {
		article {
			grid-column: 1/4;
			justify-self: center;
		}
	}
	@media (max-width: 767px) {
		article {
			/* TODO Слишком рано меняется ширина на сто.  */
			/* max-width:; не получается установить... */

			width: 100%;
			justify-self: center;
		}
	}
</style>
