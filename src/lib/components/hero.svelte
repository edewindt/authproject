<script>
	import Type from './layout/type.svelte';
	import { isLoggedIn } from '/src/routes/stores/authStore';
	import { getAuth, signOut } from 'firebase/auth';
	import { onMount } from 'svelte';
	import { blur, fly } from 'svelte/transition';
	import tree from '$lib/assets/tree.jpg';
	let ready = false;
	onMount(() => (ready = true));
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
	let style;
	if (!$isLoggedIn) {
		style = 'display:flex; justify-content:center';
	}
</script>

<div class="hero" in:blur={{ amount: 10, duration: 1000 }}>
	<img src={tree} alt="" />
	{#if ready}
		<div class="hero-text" in:fly={{ delay: 1000, duration: 1000, y: 200 }}>
			<h3><Type /></h3>
		</div>
		<div class="butt-contain" {style} in:fly={{ delay: 1000, duration: 1000, y: 200 }}>
			{#if $isLoggedIn}
				<a on:click|preventDefault={logout} href="/"><button class="butt">Sign Out</button></a><a
					href="#down"><button class="butt">Start</button></a
				><a href="/"
					><button class="butt" in:fly={{ delay: 1000, duration: 1000, y: 200 }}>About</button></a
				>
				<a href="/"
					><button class="butt" in:fly={{ delay: 1000, duration: 1000, y: 200 }}>Contact</button></a
				>
			{/if}
			{#if !$isLoggedIn}
				<a href="/login"
					><button class="butt" in:fly={{ delay: 1000, duration: 1000, y: 200 }}>Login</button></a
				>
			{/if}
		</div>
	{/if}
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
		display: grid;
		grid-template-columns: repeat(2, 1fr);
		gap: 1rem;
		margin-top: 1.3rem;
		justify-content: center;
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
			width: 12rem;
		}
		.butt-contain {
			grid-template-columns: none;
		}
	}
	.butt:hover {
		background-color: aliceblue;
		color: var(--main);
	}
</style>
