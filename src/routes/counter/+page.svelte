<script>
	$: count = 0;

	const increaseCount = () => {
		count += 1;
	};

	const decreaseCount = () => {
		count -= 1;
	};
</script>

<section id="counter">
	<h1>Simple Counter</h1>
	<span>{count}</span>
	<div>
		<button on:click={increaseCount}>Increase</button>
		<button on:click={decreaseCount}>Decrease</button>
	</div>
	<a href="/">Home Page</a>
</section>
