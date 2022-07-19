<script>
	import app from './fb';
	import { onMount } from 'svelte';
	import { getAuth, onAuthStateChanged } from 'firebase/auth';
	import { goto } from '$app/navigation';
	import Navbar from '$lib/components/layout/navbar.svelte';
	import { isLoggedIn } from './stores/authStore';
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

<Navbar />
<slot />
