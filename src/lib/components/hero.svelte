<script>
	import Type from './layout/type.svelte';
	import { isLoggedIn } from '/src/routes/stores/authStore';
	import { getAuth, signOut } from 'firebase/auth';
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

<div class="hero">
	<img src="src/tree.jpg" alt="" />
	<div class="hero-text">
		<h3><Type /></h3>
	</div>
	<div class="butt-contain">
		{#if $isLoggedIn}
			<a on:click|preventDefault={logout} href="/login"><button class="butt">Sign Out</button></a><a
				href="#down"><button class="butt">Start</button></a
			>
		{/if}
		{#if !$isLoggedIn}
			<a href="/login"><button class="butt">Login</button></a>
		{/if}
	</div>
</div>

<style>
	.hero {
		width: 100%;
		height: 100vh;
		position: relative;
		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction: column;
	}
	img {
		object-fit: cover;
		width: 100%;
		height: 100%;
		filter: brightness(-500%);
		position: absolute;
	}
	.hero-text {
		color: var(--text1);
		z-index: 1;
		font-size: 5rem;
	}
	.butt-contain {
		z-index: 1;
		display: flex;
		gap: 1rem;
	}
	.butt {
		padding: 1rem;
		font-size: 2rem;
		width: 15rem;
		background-color: transparent;
		border: solid 0.35rem var(--text1);
		color: var(--text1);
		border-radius: 1rem;
		cursor: pointer;
		transition: 0.3s;
	}
	@media only screen and (max-width: 550px) {
		.hero-text {
			font-size: 3.5rem;
		}
		.butt {
			width: 10rem;
		}
	}
	.butt:hover {
		background-color: aliceblue;
		color: var(--main);
	}
</style>
