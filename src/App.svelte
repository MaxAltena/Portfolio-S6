<script>
	import { Router, Route } from "svelte-routing";

	import FixedBanner from "./utils/FixedBanner.svelte";

	export let url = "";
	export let basepath = process.env.isProd ? "S6" : "";

	$: document.title = `${$name} ${$semester} – ${$fullName}`;
</script>

<div class="accent" role="presentation"></div>

<Router {url} {basepath}>
	<Route path="/">
		<main>
			<p>In Semester 6 zijn er twee portfolio's gemaakt.</p>
			<p>Navigeer naar ze door middel van de onderstaande links:</p>
			<ul>
				<li><a href="project1/">Project 1 (Stichting Ik Wil)</a></li>
				<li><a href="project2/">Project 2 (PIDZ)</a></li>
			</ul>
		</main>
	</Route>
</Router>

<FixedBanner />

<style>
	.accent {
		position: fixed;
		z-index: 10000;
		height: 4px;
		width: 100%;
		top: 0;
		left: 0;
		right: 0;
		background: var(--accent);
		transition: background var(--transition-speed) var(--transition-timing);
	}

	main {
		position: fixed;
		top: 0;
		right: 0;
		bottom: 0;
		left: 0;
		width: 100vw;
		min-height: 100vh;
		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction: column;
	}

	:global(hr) {
		width: 95%;
		margin: 20px auto;
		border-width: 1px;
		border-style: solid;
		border-color: var(--on-primary);
		border-radius: 999px;
		opacity: 0.25;
		transition: border-color var(--transition-speed) var(--transition-timing);
	}

	:global(a.link) {
		color: var(--on-primary);
		transition: color calc(var(--transition-speed) / 2) var(--transition-timing);
		text-decoration: none;
		position: relative;
	}

	:global(a.link::after) {
		content: "";
		position: absolute;
		bottom: -1px;
		left: -1px;
		right: -1px;
		width: calc(100% + 2px);
		height: 2px;
		border-radius: 4px;
		background: var(--accent);
		z-index: -1;
		transition: height calc(var(--transition-speed) / 2) var(--transition-timing);
	}

	:global(a.link:hover::after, a.link:active::after) {
		height: calc(100% + 2px);
	}

	:global(a.link:hover, a.link:active) {
		color: var(--primary);
	}
</style>
