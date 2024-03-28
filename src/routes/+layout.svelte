<style>
	.container {
	  width: 100%;
	  max-height: 70vh;
	  overflow-x: scroll;
	  margin-top: 20px;
	}
		
	.demo-widget {
	  background: #f1f1f1;
	  height: 100%;
	  width: 100%;
	  display: flex;
	  justify-content: center;
	  align-items: center;
	  border-radius: 8px;
	  border: 1px dashed red;
	  display: flex;
	  flex-direction: column;
	}
	</style>

	
	<div class:container={!useWindow} bind:this={container}>
	  <Grid bind:items={items} rowHeight={100} let:item let:dataItem {rows} {scroller} {sensor} {fillSpace}>
		<div class=demo-widget>
			<div class="id">{dataItem.id}</div> <br/>
			{#if item.closestEdge}
				<div class="edge-debug">{item.closestEdge?.type} edge from {item.closestEdge?.elementId}</div>
				<pre>{JSON.stringify(item, null, 2)}</pre>
			{/if}

			{#if item.providesClosestEdge}
				<div class="edge-debug">{item.providesClosestEdge.edgeType}</div>
			{/if}
		</div>
	  </Grid>
	</div>
	
	
	<script>
	import { onMount } from 'svelte';
	import Grid from "svelte-grid";
	import gridHelp from "svelte-grid/build/helper/index.mjs";
	
	const id = () => "_" + Math.random().toString(36).substr(2, 9);
	
	let container;
	let useWindow = true;
	let documentContainer;
	let fillSpace = false;
	let scroller;
	let sensor = 20;

	onMount(() => {
		documentContainer = document.documentElement;
		scroller = container;
	});

	$: scroller = useWindow ? documentContainer : container;
	
	
	let items = [
	  {
		6: gridHelp.item({
		  x: 0,
		  y: 0,
		  w: 5,
		  h: 4,
		}),
		id: id(),
	  },
	
	  {
		6: gridHelp.item({
		  x: 6,
		  y: 0,
		  w: 5,
		  h: 4,
		}),
		id: id(),
	  },
		
	  {
		6: gridHelp.item({
		  x: 12,
		  y: 0,
		  w: 4,
		  h: 2,
		}),
		id: id(),
	  },
		
	  {
		6: gridHelp.item({
		  x: 12,
		  y: 2,
		  w: 4,
		  h: 2,
		}),
		id: id(),
	  },	
	  {
		6: gridHelp.item({
		  x: 16,
		  y: 0,
		  w: 5,
		  h: 4,
		}),
		id: id(),
	  },
	  {
		6: gridHelp.item({
		  x: 200,
		  y: 0,
		  w: 1,
		  h: 1,
		}),
		id: id(),
	  },
	];
	
	const rows = [
	  [ 1100, 6 ],
	];
	</script>
	