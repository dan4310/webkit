<script lang="ts">
	import Drawer from '$lib/components/Drawer.svelte'
	import Icon from '$lib/components/Icon.svelte'
	let open = false
</script>

<button type="button" on:click={() => (open = true)}>
	<Icon name="menu" />
</button>
<Drawer {open} title="Cibus" on:close={() => (open = false)}>
	<button slot="btn-close" type="button" on:click={() => open = false}>
		<Icon name="x" />
	</button>

	<h1>Hello World</h1>
</Drawer>
