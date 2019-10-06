<script>
	let scoops = 1;
	let flavours = ['Half Square Triangle'];

	let menu = [
		'Quarter Square Triangle',
		'Half Square Triangle',
		'Half Square Rectangle'
	];

	function join(flavours) {
		if (flavours.length === 1) return flavours[0];
		return `${flavours.slice(0, -1).join(', ')} and ${flavours[flavours.length - 1]}`;
	}
</script>
<h1>A Quilt Is: </h1>
<h2>Blocks</h2>

<label>
	<input type=radio bind:group={scoops} value={1}>
	One Block
</label>

<label>
	<input type=radio bind:group={scoops} value={4}>
	Four Blocks
</label>

<label>
	<input type=radio bind:group={scoops} value={9}>
	Nine Blocks
</label>

<h2>Patches</h2>

{#each menu as flavour}
	<label>
		<input type=checkbox bind:group={flavours} value={flavour}>
		{flavour}
	</label>
{/each}

{#if flavours.length === 0}
	<p>Please select at least one patch</p>
{:else if flavours.length > scoops}
	<p>Can't create more patches than blocks!</p>
{:else}
	<p>
		You created {scoops} {scoops === 1 ? 'block' : 'blocks'}
		of {join(flavours)}
	</p>
  
  
{/if}

