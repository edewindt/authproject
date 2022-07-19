<script>
	import { goto } from '$app/navigation';
	import { getAuth, signOut } from 'firebase/auth';
	import { isLoggedIn } from '../../../routes/stores/authStore';

	const auth = getAuth();

	const logout = () => {
		signOut(auth)
			.then(() => {
				localStorage.removeItem('uid');
				goto('/login');
			})
			.catch((error) => {
				console.error(error);
			});
	};
</script>

<nav>
	<ul>
		<li class="nav-item">
			<a class="nav-link" aria-current="page" href="/">Home</a>
		</li>

		{#if $isLoggedIn}
			<li class="nav-item">
				<a class="nav-link" target="_blank" href="/">Search</a><input type="text" />
			</li>
			<li class="nav-item">
				<a class="nav-link" on:click|preventDefault={logout} target="_blank" href="/">Sign Out</a>
			</li>
		{/if}
	</ul>
</nav>

<style>
	ul {
		display: flex;
		justify-content: space-between;
		padding: 1rem;
	}
	li,
	a {
		list-style: none;
		text-decoration: none;
	}
	nav {
		background-color: var(--dark);
	}
</style>
