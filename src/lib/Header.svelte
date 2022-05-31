<script lang="ts">
	export let remaining: number;
	export let total: number;
</script>

<div class="app-header">
	<div>{total} Total</div>
	<div class="task-count">{remaining} Remaining</div>
</div>

<style>
	.app-header {
		padding: 10px;
		display: flex;
		justify-content: space-between;
	}

	.task-count {
		align-self: center;
	}
</style>
