<script lang="ts">
	export let colors: Record<string, Record<string, string>>;
	export let splitAmount: number;

	function copyToClipboard(hex: string) {
		navigator.clipboard.writeText(hex);
	}

	function weightToTextColor(weight: string) {
		switch (weight) {
			case '50':
			case '100':
			case '200':
			case '300':
			case '400':
				return '#000';
			case '500':
			case '600':
			case '700':
			case '800':
			case '900':
				return '#fff';
			default:
				return '#000';
		}
	}
</script>

<div class="colors" style:grid-template-columns={`repeat(${splitAmount}, 1fr)`}>
	{#each Object.entries(colors) as [name, color]}
		{@const titleCaseName = name
			.replace(/([A-Z])/g, ' $1')
			.replace(/^./, (str) => str.toUpperCase())}
		<div class="container">
			<h2 style:color={Object.values(color)[5]}>{titleCaseName}</h2>
			<div class="color-wall">
				{#each Object.entries(color).reverse() as [weight, hex]}
					<button
						class="color"
						style:background={hex}
						style:color={hex}
						on:click={() => copyToClipboard(hex)}
						><span style:color={weightToTextColor(weight)}>{weight}</span></button
					>
				{/each}
			</div>
		</div>
	{/each}
</div>

<style>
	.container {
		margin: 0.5rem;
		text-align: center;
	}

	button.color span {
		color: white;
		font-size: 0.5rem;
	}

	button.color {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		width: 100%;
		height: 1rem;
		border: none;
		cursor: pointer;
	}

	button.color:hover {
		filter: brightness(0.8);
	}

	button.color:active {
		filter: brightness(0.6);
	}

	div.color-wall {
		display: flex;
		width: fit-content;
		flex-direction: column;
		margin: 1rem 0;
		width: 100%;
		border-radius: 1rem;
		overflow: hidden;
	}

	.colors {
		display: grid;
		grid-gap: 1rem;
	}

	h2 {
		margin: 0;
		padding: 0;
		font-size: 1rem;
	}
</style>
