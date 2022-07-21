<script>
	import { goto } from '$app/navigation';
	import {
		getAuth,
		signInWithEmailAndPassword,
		createUserWithEmailAndPassword
	} from 'firebase/auth';
	export let title;
	import tree from '$lib/assets/tree.jpg';
	const auth = getAuth();

	const login = () => {
		let email = document.getElementById('emailInput').value;
		let password = document.getElementById('passInput').value;

		if (title == 'Login') {
			signInWithEmailAndPassword(auth, email, password)
				.then((userCredential) => {
					const user = userCredential.user;
					localStorage.setItem('uid', user.uid);
					goto('/');
				})
				.catch((error) => {
					console.error(error);
				});
		} else {
			createUserWithEmailAndPassword(auth, email, password)
				.then((userCredential) => {
					const user = userCredential.user;
					localStorage.setItem('uid', user.uid);
					goto('/');
				})
				.catch((error) => {
					console.error(error);
				});
		}
	};
	let col = '';
</script>

<div class="body">
	<div class="contain">
		<div class="login">
			<div class="card">
				<div class="login-form">
					<h5 class="card-title">{title}</h5>
					<form on:submit|preventDefault={login}>
						<div class="emailfield">
							<label for="emailInput" class="form-label" class:red={col === 'email'}
								>Email address</label
							>
							<div class="form">
								<input
									on:click={() => (col = 'email')}
									type="email"
									class="form-control"
									id="emailInput"
									aria-describedby="emailHelp"
									placeholder="Email Address"
								/>
							</div>
						</div>
						<div class="passfield">
							<label for="passInput" class="form-label" class:red={col === 'pass'}>Password</label>
							<div class="form">
								<input
									on:click={() => (col = 'pass')}
									type="password"
									class="form-control"
									id="passInput"
									placeholder="Password"
								/>
							</div>
						</div>
						<button type="submit" class="btn btn-primary">Submit</button>
					</form>
					{#if title == 'Login'}
						<p class="form-text">
							Not a user? <a href="/signup" class="card-link">Sign Up</a>
						</p>
					{/if}
					{#if title != 'Login'}
						<div id="emailHelp" class="form-text">
							We'll never share<br /> your email with anyone else.
						</div>
					{/if}
				</div>
			</div>
			<div class="login-hero"><img src={tree} alt="" /></div>
		</div>
	</div>
</div>

<style>
	img {
		max-width: 100%;
		height: 100%;
		object-fit: cover;
		border-radius: 1rem;
	}
	.card {
		height: 50vh;
		display: flex;
		justify-content: center;
		align-items: center;
		font-size: 1.4rem;
		color: var(--text1);
	}
	a {
		text-decoration: none;
		color: red;
	}
	a:hover {
		color: var(--main);
		text-shadow: 0 0 1rem;
	}
	.passfield {
		margin-top: 1rem;
		display: flex;
		justify-content: space-between;
		color: var(--text1);
	}
	.emailfield {
		display: flex;
		justify-content: space-between;
		color: var(--text1);
	}
	.form-control {
		width: 100%;
		height: 100%;
		border: none;
		padding-left: 1rem;
	}
	.form {
		padding-left: 2rem;
	}
	.form-control:focus {
		outline: none;
		background-color: rgb(255, 126, 180);
		color: var(--text1);
		box-shadow: 0 0 1rem var(--main);
	}
	.red {
		color: var(--main);
		text-shadow: 0 0 1rem;
	}
	.card-title {
		color: red;
		font-size: 2rem;
	}
	button {
		padding: 0.5rem;
		width: 5rem;
		background-color: transparent;
		color: var(--text);
		text-shadow: 0 0 0.5rem;
		border: solid 0.2rem red;
		border-radius: 0.3rem;
		margin-top: 1rem;
		cursor: pointer;
	}
	.form-text {
		text-align: center;
		position: relative;
		top: 1.5rem;
		text-shadow: 0 0 2rem black;
	}
	button:hover {
		background-color: var(--main);
		border: solid 0.2rem var(--main);
		box-shadow: 0 0 1rem var(--main);
	}
	.login {
		width: 60rem;
		height: 50vh;
		margin: auto;
		background-color: var(--dark);
		display: grid;
		grid-template-columns: repeat(2, 1fr);
		box-shadow: 0 0 2rem var(--main);
		border-radius: 1rem;
	}
	.contain {
		height: 50rem;
		display: flex;
		justify-content: center;
	}
	@media only screen and (max-width: 1000px) {
		.login {
			width: 30rem;
			height: 30rem;
			max-width: calc(100vw - 3rem);
			display: grid;
			grid-template-columns: 1fr;
			grid-template-rows: repeat(2, 1fr);
		}
		.contain {
			height: 40rem;
		}
	}
	@media only screen and (max-width: 400px) {
		.card {
			font-size: 1rem;
		}
		.card-title {
			font-size: 1.5rem;
		}
	}
	.body {
		height: 100vh;
		background-color: rgba(91, 80, 111, 0.678);
	}
</style>
