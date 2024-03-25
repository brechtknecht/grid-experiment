<style>
	.container {
	  width: 100%;
	  max-height: 100vh;
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
	}
	</style>
	
	<label>
	  <input type="checkbox"  bind:checked={useWindow} />
	  Use document
	</label>
	
	<label>
	Sensor value
	<input type=number bind:value={sensor} />
	</label>
	
	<div class:container={!useWindow} bind:this={container}>
	  <Grid bind:items={items} rowHeight={100} let:item let:dataItem {cols} {scroller} {sensor}>
		<div class=demo-widget>{dataItem.id}</div>
	  </Grid>
	</div>
	
	
	<script>
	import { onMount } from 'svelte'
	import Grid from "svelte-grid";
	import gridHelp from "svelte-grid/build/helper/index.mjs";
	
	const id = () => "_" + Math.random().toString(36).substr(2, 9);
	
	let container;
	let useWindow = false
	let documentContainer;
	let scroller;
	let sensor = 20;
	
	onMount(() => {
	 documentContainer = document.documentElement;
	 scroller = container;
	})
	
	$: scroller = useWindow ? documentContainer : container;
	
	
	let items = [
	  {
		6: gridHelp.item({
		  x: 0,
		  y: 0,
		  w: 2,
		  h: 20,
		}),
		id: id(),
	  },
	
	  {
		6: gridHelp.item({
		  x: 2,
		  y: 0,
		  w: 2,
		  h: 2,
		}),
		id: id(),
	  },
		
	  {
		6: gridHelp.item({
		  x: 2,
		  y: 0,
		  w: 2,
		  h: 2,
		}),
		id: id(),
	  },
		
	  {
		6: gridHelp.item({
		  x: 2,
		  y: 0,
		  w: 2,
		  h: 2,
		}),
		id: id(),
	  },
		
	  {
		6: gridHelp.item({
		  x: 2,
		  y: 0,
		  w: 2,
		  h: 2,
		}),
		id: id(),
	  },
	];
	
	const cols = [
	  [ 1100, 6 ],
	];
	</script>
	