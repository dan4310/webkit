<script lang="ts">
	import { Dialog, DialogOverlay, DialogTitle } from '@rgossiaux/svelte-headlessui'
	import { createEventDispatcher } from 'svelte'
	import { fly } from 'svelte/transition'

	export let open = false
	export let title = ''
	const dispatch = createEventDispatcher()
</script>

<Dialog {open} on:close={() => dispatch('close')}>
	<DialogOverlay
		style={'position:fixed; top: 0; left: 0; background-color: var(--clr-shadow); height: 100vh; width: 100vw;'}
	/>
	<div
		class="dialog"
		transition:fly={{
			x: -200,
			duration: 200
		}}
	>
		<div class="dialog__header">
			<slot name="btn-close" />
			{#if title}
				<DialogTitle>{title}</DialogTitle>
			{/if}
		</div>
		<div class="dialog__body">
			<slot />
		</div>
	</div>
</Dialog>

<style>
	.dialog {
		position: fixed;
		top: 0;
		left: 0;
		height: 100vh;
		background-color: var(--clr-bg-1);
		padding: 0.5rem;
	}
	.dialog .dialog__header {
		display: flex;
		align-items: center;
		gap: 0.5rem;
	}
</style>
