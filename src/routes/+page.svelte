<script lang="ts">
	import * as rawColors from 'twind/colors';
	import Colors from '../lib/Colors.svelte';

	let sortedColors = {
		pink: rawColors.pink,
		rose: rawColors.rose,
		red: rawColors.red,
		orange: rawColors.orange,
		amber: rawColors.amber,
		lime: rawColors.lime,
		green: rawColors.green,
		emerald: rawColors.emerald,
		teal: rawColors.teal,
		cyan: rawColors.cyan,
		sky: rawColors.sky,
		blue: rawColors.blue,
		indigo: rawColors.indigo,
		violet: rawColors.violet,
		purple: rawColors.purple,
		fuchsia: rawColors.fuchsia
	} satisfies Record<string, Record<string, string>>;

	const grayColors = {
		gray: rawColors.gray,
		coolGray: rawColors.coolGray,
		trueGray: rawColors.trueGray,
		warmGray: rawColors.warmGray
	} satisfies Record<string, Record<string, string>>;
</script>

<main>
	<h1><a href="https://twind.dev/">Twind</a> Colors</h1>
	<h2>Source @ <a href="https://github.com/LeoDog896/twind-colors">GitHub</a>. Click to copy colors</h2>

	<Colors colors={sortedColors} splitAmount={Object.keys(sortedColors).length / 2} />
	<Colors colors={grayColors} splitAmount={Object.keys(grayColors).length} />
</main>

<style>
	h2 {
		margin: 0 6rem;
		margin-bottom: 2rem;
		padding: 0;
		font-size: 1.5rem;
		text-align: center;
		width: calc(100% - 6rem * 2);
		font-weight: 400;
		color: #555;
	}

	h1 {
		margin: 0 6rem;
		margin-bottom: 1rem;
		padding: 0;
		font-size: 4rem;
		text-align: center;
		width: calc(100% - 6rem * 2);
		font-weight: 800;
		color: #222;
	}

	a {
		color: #43a399;
		text-decoration: none;
	}
</style>
