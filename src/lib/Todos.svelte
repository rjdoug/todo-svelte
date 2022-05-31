<script>
	import Todo from '$lib/Todo.svelte';
</script>

<!-- List of actual todos -->
<div class="app-body">
	<ul>
		<Todo />
		<Todo />
	</ul>
</div>

<style>
	.app-body {
		flex-grow: 1;
		max-height: 600px;
		overflow-x: hidden;
	}

	ul {
		list-style-type: none;
		-webkit-padding-start: 0;
		padding-left: 0px;
	}
</style>
