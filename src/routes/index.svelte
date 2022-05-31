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

	let formText = '';

	// todoChecked inverts the compelete status of the give todoID
	function todoCheck(todoID: number) {
		todos.map((todo) => {
			if (todo.id === todoID) todo.completed = !todo.completed;
		});
		todos = todos;
	}

	// todoDelete will delete the todo of the given id
	function todoDelete(todoID: number) {
		todos = todos.filter((todo) => {
			return todo.id != todoID;
		});
	}

	function addTodo() {
		let id = Math.max(...todos.map((todo) => todo.id)) + 1;
		let todo: Todo = {
			id: id,
			text: formText,
			completed: false
		};
		todos.push(todo);
		formText = '';
		todos = todos
	}
</script>

<div id="app-container" class="app-container">
	<Header />
	<Todos
		{todos}
		on:check={(e) => todoCheck(e.detail.id)}
		on:deleted={(e) => todoDelete(e.detail.id)}
	/>
	<Form
		bind:text={formText}
		on:addTodo={() => {
			addTodo();
		}}
	/>
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
