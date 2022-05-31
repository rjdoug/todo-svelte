<script lang="ts">
	import Todos from '$lib/Todos.svelte';
	import Form from '$lib/Form.svelte';
	import Header from '$lib/header.svelte';
	import type { Todo } from '$lib/types/Todo';

	let todos: Todo[] = [
		{
			id: 1,
			text: 'First Todo',
			completed: true
		},
		{
			id: 2,
			text: 'Second Todo',
			completed: false
		},
		{
			id: 3,
			text: 'Third Todo',
			completed: true
		}
	];

	// todoChecked inverts the compelete status of the give todoID
	function todoCheck(todoID: number) {
		todos.map((todo) => {
			if (todo.id === todoID) todo.completed = !todo.completed;
		});
		todos = todos;
	}

	function todoDelete(todoID: number) {
		todos = todos.filter((todo) => {
			return todo.id != todoID;
		});
	}
</script>

<div id="app-container" class="app-container">
	<Header />
	<Todos
		{todos}
		on:check={(e) => todoCheck(e.detail.id)}
		on:deleted={(e) => todoDelete(e.detail.id)}
	/>
	<Form />
</div>

<style>
	.app-container {
		width: 400px;
		min-height: 500px;
		background-color: #282c34;
		box-shadow: 0 20px 80px rgba(0, 0, 0, 0.6);
		background: radial-gradient(circle, #282c34 0%, rgba(40, 48, 56, 1) 100%);
		position: relative;
		border-radius: 1em;
		padding: 20px;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
	}
</style>
