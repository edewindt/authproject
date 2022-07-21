<script>
	let y;
	import { blur, fly } from 'svelte/transition';
</script>

<svelte:window bind:scrollY={y} />
<div id="down" class="he">
	{#if y >= 700}
		<div class="inner">
			<h3 class="init" in:blur={{ amount: 10, duration: 1000 }}>Lets Get Started Shall We?</h3>
			<p in:fly={{ delay: 1000, duration: 1000, y: 100 }}>
				You can navigate through this website by scrolling, the menu bar in the middle of the
				navigation also allows you navigation, it has a searchbar at the top dispite looking ugly.
			</p>
		</div>
	{/if}
</div>
<div id="about" class="he">
	{#if y >= 1400}
		<div class="inner">
			<h3 class="init" in:blur={{ amount: 10, duration: 1000 }}>
				This App Was Made to Test Authentication
			</h3>
			<p in:fly={{ delay: 1000, duration: 1000, y: 100 }}>
				I then got carried away styling the login page, and eventually went into designing other
				aspects of the website including the animations, navigation, and the User Interface as a
				whole.
			</p>
		</div>
	{/if}
</div>

<style>
	.he {
		height: 100vh;
		display: grid;
		justify-content: center;
		align-items: center;
		font-size: 3rem;
		text-align: center;
	}
	.inner {
		width: 60rem;
		max-width: calc(100vw - 5rem);
	}
	.init {
		margin-bottom: 1rem;
	}
	@media only screen and (max-width: 600px) {
		.he {
			font-size: 2rem;
		}
	}
</style>
