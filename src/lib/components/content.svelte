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
			<div class="butts"><a href="#about"><button class="butt">Next</button></a></div>
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
				whole. It's layout is fully responsive on everything but an iPad (trust me I tried).
			</p>
			<div class="butts"><a href="#app"><button class="butt">Next</button></a></div>
		</div>
	{/if}
</div>
<div id="app" class="he">
	{#if y >= 2100}
		<div class="inner">
			<h3 class="init" in:blur={{ amount: 10, duration: 1000 }}>
				It was all done with Svelte and Firebase
			</h3>
			<div class="img" in:fly={{ delay: 1000, duration: 1000, y: 100 }}>
				<svg
					viewBox="0 0 256 351"
					xmlns="http://www.w3.org/2000/svg"
					xmlns:xlink="http://www.w3.org/1999/xlink"
					preserveAspectRatio="xMidYMid"
					><defs
						><path
							d="M1.253 280.732l1.605-3.131 99.353-188.518-44.15-83.475C54.392-1.283 45.074.474 43.87 8.188L1.253 280.732z"
							id="a"
						/><filter
							x="-50%"
							y="-50%"
							width="200%"
							height="200%"
							filterUnits="objectBoundingBox"
							id="b"
							><feGaussianBlur
								stdDeviation="17.5"
								in="SourceAlpha"
								result="shadowBlurInner1"
							/><feOffset in="shadowBlurInner1" result="shadowOffsetInner1" /><feComposite
								in="shadowOffsetInner1"
								in2="SourceAlpha"
								operator="arithmetic"
								k2="-1"
								k3="1"
								result="shadowInnerInner1"
							/><feColorMatrix
								values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0.06 0"
								in="shadowInnerInner1"
							/></filter
						><path
							d="M134.417 148.974l32.039-32.812-32.039-61.007c-3.042-5.791-10.433-6.398-13.443-.59l-17.705 34.109-.53 1.744 31.678 58.556z"
							id="c"
						/><filter
							x="-50%"
							y="-50%"
							width="200%"
							height="200%"
							filterUnits="objectBoundingBox"
							id="d"
							><feGaussianBlur
								stdDeviation="3.5"
								in="SourceAlpha"
								result="shadowBlurInner1"
							/><feOffset
								dx="1"
								dy="-9"
								in="shadowBlurInner1"
								result="shadowOffsetInner1"
							/><feComposite
								in="shadowOffsetInner1"
								in2="SourceAlpha"
								operator="arithmetic"
								k2="-1"
								k3="1"
								result="shadowInnerInner1"
							/><feColorMatrix
								values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0.09 0"
								in="shadowInnerInner1"
							/></filter
						></defs
					><path
						d="M0 282.998l2.123-2.972L102.527 89.512l.212-2.017L58.48 4.358C54.77-2.606 44.33-.845 43.114 6.951L0 282.998z"
						fill="#FFC24A"
					/><use fill="#FFA712" fill-rule="evenodd" xlink:href="#a" /><use
						filter="url(#b)"
						xlink:href="#a"
					/><path
						d="M135.005 150.38l32.955-33.75-32.965-62.93c-3.129-5.957-11.866-5.975-14.962 0L102.42 87.287v2.86l32.584 60.233z"
						fill="#F4BD62"
					/><use fill="#FFA50E" fill-rule="evenodd" xlink:href="#c" /><use
						filter="url(#d)"
						xlink:href="#c"
					/><path
						fill="#F6820C"
						d="M0 282.998l.962-.968 3.496-1.42 128.477-128 1.628-4.431-32.05-61.074z"
					/><path
						d="M139.121 347.551l116.275-64.847-33.204-204.495c-1.039-6.398-8.888-8.927-13.468-4.34L0 282.998l115.608 64.548a24.126 24.126 0 0 0 23.513.005"
						fill="#FDE068"
					/><path
						d="M254.354 282.16L221.402 79.218c-1.03-6.35-7.558-8.977-12.103-4.424L1.29 282.6l114.339 63.908a23.943 23.943 0 0 0 23.334.006l115.392-64.355z"
						fill="#FCCA3F"
					/><path
						d="M139.12 345.64a24.126 24.126 0 0 1-23.512-.005L.931 282.015l-.93.983 115.607 64.548a24.126 24.126 0 0 0 23.513.005l116.275-64.847-.285-1.752-115.99 64.689z"
						fill="#EEAB37"
					/></svg
				>+<img src="src/svelte.png" alt="" />
			</div>
			<div class="butts"><a href="#end"><button class="butt">Next</button></a></div>
		</div>
	{/if}
</div>
<div id="end" class="he">
	{#if y >= 3000}
		<div class="inner">
			<h3 class="init" in:blur={{ amount: 10, duration: 1000 }}>The End</h3>
			<p in:fly={{ delay: 1000, duration: 1000, y: 100 }}>
				You've reached the end, I wasn't creative enough to add more to this.
			</p>
		</div>
	{/if}
</div>

<style>
	:root {
		--img-width: 7rem;
		scroll-behavior: smooth;
	}
	.he {
		height: 100vh;
		display: grid;
		justify-content: center;
		align-items: center;
		font-size: 3rem;
		text-align: center;
		background-color: rgba(208, 191, 238, 0.678);
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
	.img {
		display: flex;
		flex-direction: row-reverse;
		justify-content: center;
		align-items: center;
		font-size: 10rem;
	}
	.img svg {
		width: var(--img-width);
	}
	.img img {
		width: var(--img-width);
	}
	.butt {
		border: none;
		padding: 1rem;
		background-color: aliceblue;
		width: 10rem;
		font-size: 3rem;
	}
	.butts {
		margin-top: 2rem;
	}
</style>
