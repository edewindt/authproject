<script>
	import { goto } from '$app/navigation';
	import { getAuth, signOut } from 'firebase/auth';
	import { isLoggedIn } from '../../../routes/stores/authStore';
	import Menu from '../menu.svelte';
	const auth = getAuth();
	const menuitems = [
		'About',
		'Art',
		'Blog',
		'Contact',
		'Cookie Policy',
		'Culture',
		'Support',
		'Tools',
		'Products',
		'Pricing',
		'FAQ',
		'Music',
		'Projects',
		'Terms of Use',
		'Privacy Policy',
		'News'
	];

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
	let filtered = [];
	let inputval = '';
	const filter = () => {
		filtered = menuitems.filter((item) => item.toLowerCase().includes(inputval.toLowerCase()));
	};
</script>

<nav>
	<ul>
		<li class="nav-item">
			<a class="nav-link" aria-current="page" href="/"
				><svg class="nav-svg house" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 576 512"
					><!--! Font Awesome Pro 6.1.1 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license (Commercial License) Copyright 2022 Fonticons, Inc. --><path
						d="M575.8 255.5C575.8 273.5 560.8 287.6 543.8 287.6H511.8L512.5 447.7C512.5 450.5 512.3 453.1 512 455.8V472C512 494.1 494.1 512 472 512H456C454.9 512 453.8 511.1 452.7 511.9C451.3 511.1 449.9 512 448.5 512H392C369.9 512 352 494.1 352 472V384C352 366.3 337.7 352 320 352H256C238.3 352 224 366.3 224 384V472C224 494.1 206.1 512 184 512H128.1C126.6 512 125.1 511.9 123.6 511.8C122.4 511.9 121.2 512 120 512H104C81.91 512 64 494.1 64 472V360C64 359.1 64.03 358.1 64.09 357.2V287.6H32.05C14.02 287.6 0 273.5 0 255.5C0 246.5 3.004 238.5 10.01 231.5L266.4 8.016C273.4 1.002 281.4 0 288.4 0C295.4 0 303.4 2.004 309.5 7.014L564.8 231.5C572.8 238.5 576.9 246.5 575.8 255.5L575.8 255.5z"
					/></svg
				></a
			><a class="nav-link nav-text" aria-current="page" href="/">Home</a>
		</li>
		{#if !$isLoggedIn}
			<li class="nav-item">
				<a class="nav-link nav-text" on:click|preventDefault={logout} target="_blank" href="/"
					>Log In
				</a><a class="nav-link" on:click|preventDefault={logout} target="_blank" href="/"
					><svg class="nav-svg signout" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"
						><!--! Font Awesome Pro 6.1.1 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license (Commercial License) Copyright 2022 Fonticons, Inc. --><path
							d="M160 416H96c-17.67 0-32-14.33-32-32V128c0-17.67 14.33-32 32-32h64c17.67 0 32-14.33 32-32S177.7 32 160 32H96C42.98 32 0 74.98 0 128v256c0 53.02 42.98 96 96 96h64c17.67 0 32-14.33 32-32S177.7 416 160 416zM502.6 233.4l-128-128c-12.51-12.51-32.76-12.49-45.25 0c-12.5 12.5-12.5 32.75 0 45.25L402.8 224H192C174.3 224 160 238.3 160 256s14.31 32 32 32h210.8l-73.38 73.38c-12.5 12.5-12.5 32.75 0 45.25s32.75 12.5 45.25 0l128-128C515.1 266.1 515.1 245.9 502.6 233.4z"
						/></svg
					></a
				>
			</li>
		{/if}
		{#if $isLoggedIn}
			<div class="dropdown">
				<li class="nav-item">
					<a class="nav-link" href="/"
						><svg class="nav-svg search" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512"
							><!--! Font Awesome Pro 6.1.1 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license (Commercial License) Copyright 2022 Fonticons, Inc. --><path
								d="M0 96C0 78.33 14.33 64 32 64H416C433.7 64 448 78.33 448 96C448 113.7 433.7 128 416 128H32C14.33 128 0 113.7 0 96zM0 256C0 238.3 14.33 224 32 224H416C433.7 224 448 238.3 448 256C448 273.7 433.7 288 416 288H32C14.33 288 0 273.7 0 256zM416 448H32C14.33 448 0 433.7 0 416C0 398.3 14.33 384 32 384H416C433.7 384 448 398.3 448 416C448 433.7 433.7 448 416 448z"
							/></svg
						></a
					><a class="nav-link nav-text" href="/">Menu</a>
				</li>
				<div class="drop-cont">
					<div class="some">
						<input
							class="inp"
							type="text"
							placeholder="Search"
							on:keyup={filter}
							bind:value={inputval}
						/>
						{#if filtered.length > 0}
							{#each filtered as item}
								<Menu label={item} />
							{/each}
						{:else}
							{#each menuitems as item}
								<Menu label={item} />
							{/each}
						{/if}
					</div>
				</div>
			</div>
			<li class="nav-item">
				<a class="nav-link nav-text" on:click|preventDefault={logout} target="_blank" href="/"
					>Sign Out
				</a><a class="nav-link" on:click|preventDefault={logout} target="_blank" href="/"
					><svg class="nav-svg signout" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"
						><!--! Font Awesome Pro 6.1.1 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license (Commercial License) Copyright 2022 Fonticons, Inc. --><path
							d="M160 416H96c-17.67 0-32-14.33-32-32V128c0-17.67 14.33-32 32-32h64c17.67 0 32-14.33 32-32S177.7 32 160 32H96C42.98 32 0 74.98 0 128v256c0 53.02 42.98 96 96 96h64c17.67 0 32-14.33 32-32S177.7 416 160 416zM502.6 233.4l-128-128c-12.51-12.51-32.76-12.49-45.25 0c-12.5 12.5-12.5 32.75 0 45.25L402.8 224H192C174.3 224 160 238.3 160 256s14.31 32 32 32h210.8l-73.38 73.38c-12.5 12.5-12.5 32.75 0 45.25s32.75 12.5 45.25 0l128-128C515.1 266.1 515.1 245.9 502.6 233.4z"
						/></svg
					></a
				>
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
		font-size: 1.25rem;
		color: var(--text1);
		transition: 0.3s;
	}
	nav {
		background-color: var(--dark);
		box-shadow: 0 0 2rem var(--main);
	}
	.nav-svg {
		width: 1.5rem;
		fill: red;
		transition: 0.3s;
	}
	.nav-item {
		display: flex;
	}
	.house {
		margin-right: 1rem;
	}
	.signout {
		margin-left: 1rem;
	}
	.search {
		margin-right: 1rem;
	}
	@media only screen and (max-width: 550px) {
		.nav-text {
			display: none;
		}
	}
	a:hover {
		color: var(--main);
		text-shadow: 0 0 0.5rem;
	}
	.nav-item:hover .nav-svg {
		fill: var(--main);
		text-shadow: 0 0 0.5rem;
	}
	.dropdown {
		position: relative;
	}
	.drop-cont {
		display: none;
		position: absolute;
	}
	.dropdown:hover .drop-cont {
		display: block;
	}
	.inp {
		height: 2rem;
		border-top-left-radius: 0.5rem;
		border-top-right-radius: 0.5rem;
		text-align: center;
		border: none;
	}
	.inp:focus {
		outline: none;
	}
</style>
