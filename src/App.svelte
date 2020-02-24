<script>
import Topbar from "./Topbar.svelte";
import Bottombar from "./Bottombar.svelte";

window.SpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition;

const spell = new SpeechRecognition();

spell.addEventListener('result', e =>{
	const transcript = Array.from(e.results)
	.map(result => result[0])
	.map(result => result.transcript)
	.join('');
	console.log(transcript);
	if (transcript === "Knox") {
		document.body.style = "background-color: black;"
	}
	else if (transcript === "lumos") {
		document.body.style = "background-color: white;"
	}
})

spell.addEventListener('end', spell.start)

spell.start();

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