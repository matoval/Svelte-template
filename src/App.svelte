<script>
import Topbar from "./Topbar.svelte";
import Bottombar from "./Bottombar.svelte";

</script>

<main id="whole-page">
	<header>
		<Topbar></Topbar>
	</header>
	<div id="main">
	</div>
	<footer>
		<Bottombar></Bottombar>
	</footer>
</main>

<style>
	main {
		min-height: 95vh;
	}
	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>