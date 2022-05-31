<script lang="ts">
	import Todo from '$lib/Todo.svelte';
	import type { Todo as todo } from '$lib/types/Todo';
	import { text } from 'svelte/internal';

	export let todos: todo[];
</script>

<!-- List of actual todos -->
<div class="app-body">
	<ul>
		{#each todos as t}
			<Todo text={t.text} />
		{/each}
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
