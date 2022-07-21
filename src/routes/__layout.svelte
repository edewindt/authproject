<script>
	import '/src/global.css';
	import app from './fb';
	import { onMount } from 'svelte';
	import { getAuth, onAuthStateChanged } from 'firebase/auth';
	import { goto } from '$app/navigation';
	import Navbar from '$lib/components/layout/navbar.svelte';
	import { isLoggedIn } from './stores/authStore';
	let ready = false;
	onMount(() => (ready = true));

	onMount(() => {
		const auth = getAuth();
		onAuthStateChanged(auth, (user) => {
			if (user) {
				console.log('Welcome to authentication');
				isLoggedIn.update(() => true);
			} else {
				isLoggedIn.update(() => false);
				goto('/login');
			}
		});
	});
</script>

{#if ready}
	<div class="stick"><Navbar /></div>
	<slot />
{/if}

<style>
	.stick {
		position: fixed;
		width: 100%;
		z-index: 2;
	}
</style>
