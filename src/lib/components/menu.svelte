<script>
	export let label;
</script>

<li><a href="#{label.toLowerCase()}">{label}</a></li>

<style>
	li {
		display: block;
		text-align: center;
		background-color: var(--dark);
		padding: 0.5rem;
		border-top: 0.1rem solid rgba(201, 201, 201, 0.292);
	}
	a {
		color: var(--text1);
		padding: 0.5rem;
		display: block;
	}
	li:last-child {
		border-bottom-left-radius: 1rem;
		border-bottom-right-radius: 1rem;
	}
	a:hover {
		color: var(--main);
		text-shadow: 0 0 1rem;
	}
	li:hover {
		box-shadow: 0 0 1rem var(--main);
		border: 0.1rem solid var(--main);
	}
</style>
