<script lang="ts">
	import { Canvas } from '@threlte/core';
	import { Studio } from '@threlte/studio';
	import type CameraControls from '$lib/components/CameraControls.svelte';
	import Scene from '$lib/components/Scene.svelte';
	import { Checkbox, Pane } from 'svelte-tweakpane-ui';

	let controls: CameraControls;
</script>

<Pane title="Camera Controls" position="fixed">
	{#if controls !== undefined}
		<Checkbox bind:value={controls.enabled} label="enabled" />
	{/if}
</Pane>

<div class="h-screen w-screen">
	<Canvas>
		<Studio>
			<Scene bind:controls />
		</Studio>
	</Canvas>
</div>
