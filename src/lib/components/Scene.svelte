<script lang="ts">
	import { T, useThrelte } from '@threlte/core';
	import Tree from '$lib/components/models/tree1.svelte';
	import type CC from 'camera-controls';
	import CameraControls from '$lib/components/CameraControls.svelte';
	import { PerspectiveCamera } from 'three';

	type Props = {
		controls: CC;
	};

	let { controls = $bindable() }: Props = $props();

	const { dom } = useThrelte();

	const camera = new PerspectiveCamera();
	controls = new CameraControls(camera, dom);
	controls.setLookAt(10, 10, 10, 0, 0, 0, false);
	controls.enabled = false;
</script>

<T is={camera} makeDefault />

<T.DirectionalLight position={[3, 10, 7]} />
<T.AmbientLight />

<T.Group position={[-3.3, 0, 2.7]} visible>
	<Tree />
</T.Group>

<T.Mesh rotation={[-1.5708, 0, 0]}>
	<T.PlaneGeometry args={[10, 10, 10, 10]} />
	<T.MeshStandardMaterial color="#3eb964" />
</T.Mesh>

<T.Mesh position={[3.8, 0.7, 0]}>
	<T.BoxGeometry />
	<T.MeshStandardMaterial />
</T.Mesh>
