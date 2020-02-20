<script>
import Header from "./Header.svelte";
import Footer from "./Footer.svelte";
	
</script>

<main>
	<div class="header">
		<Header></Header>
	</div>
	<div class="main">
	</div>
	<div class="footer">
		<Footer></Footer>
	</div>
</main>

<style>
	.main {
		min-height: 95vh;
	}
	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>