<script lang="ts">
	import Dropdown from '$lib/components/dropdown/Dropdown.svelte';
	import type { Hst } from '@histoire/plugin-svelte';
	export let Hst: Hst;
</script>

<Hst.Story>
	<Dropdown label="Dropdown" />
</Hst.Story>
