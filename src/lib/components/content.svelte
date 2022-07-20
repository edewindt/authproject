<script>
	let y;
	import { blur } from 'svelte/transition';
</script>

<svelte:window bind:scrollY={y} />
<div class="he">
	<img id="down" transition:blur={{ amount: 10, duration: 1000 }} src="/src/jeor.webp" alt="" />
</div>

<style>
	.he {
		height: 100vh;
		display: flex;
		justify-content: center;
		align-items: center;
	}
</style>
