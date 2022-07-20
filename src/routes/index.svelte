<script>
	import Hero from '../lib/components/hero.svelte';
	import Content from '../lib/components/content.svelte';
	import { isLoggedIn } from './stores/authStore';
</script>

<Hero />
{#if $isLoggedIn}
	<Content />
{/if}
