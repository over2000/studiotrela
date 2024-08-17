<script>
	import { onMount } from 'svelte';

	let asciiArt = `
	
	Ⲧ ℛ ᙓ ᥨ ລ 
	𝖘𝖎𝖙𝖊 
	𝖇𝖞 
	བཔཇའ 💋ྀིྀི Ⲧ ℛ ᙓ ᥨ ລ 
	𝖘𝖎𝖙𝖊 
	𝖇𝖞 
	བཔཇའ 💋ྀིྀི Ⲧ ℛ ᙓ ᥨ ລ 
	𝖘𝖎𝖙𝖊 
	𝖇𝖞 
	བཔཇའ 💋ྀིྀི Ⲧ ℛ ᙓ ᥨ ລ 
	𝖘𝖎𝖙𝖊 
	𝖇𝖞 
	བཔཇའ 💋ྀིྀི Ⲧ ℛ ᙓ ᥨ ລ 
	𝖘𝖎𝖙𝖊 
	𝖇𝖞 
	བཔཇའ 💋ྀིྀི Ⲧ ℛ ᙓ ᥨ ລ 
	𝖘𝖎𝖙𝖊 
	𝖇𝖞 
	བཔཇའ 💋ྀིྀི Ⲧ ℛ ᙓ ᥨ ລ 
	𝖘𝖎𝖙𝖊 
	𝖇𝖞 
	བཔཇའ 💋ྀིྀི Ⲧ ℛ ᙓ ᥨ ລ 
	𝖘𝖎𝖙𝖊 
	𝖇𝖞 
	བཔཇའ 💋ྀིྀི Ⲧ ℛ ᙓ ᥨ ລ 
	𝖘𝖎𝖙𝖊 
	𝖇𝖞 
	བཔཇའ 💋ྀིྀི 
	`;

	let characters = [];

	onMount(() => {
		// Quebrando a arte ASCII em caracteres individuais
		characters = [...asciiArt.replace(/\n/g, '')].map((char, index) => ({
			char,
			x: Math.random() * (window.innerWidth - 20), // Ajusta o intervalo para evitar que os caracteres saiam da tela
			y: Math.random() * (window.innerHeight - 20),
			vx: (Math.random() - 0.5) * 2, // Velocidade aleatória X
			vy: (Math.random() - 0.5) * 2, // Velocidade aleatória Y
			id: index
		}));

		function update() {
			characters = characters.map(c => {
				let { x, y, vx, vy } = c;

				// Atualiza posição
				x += vx;
				y += vy;

				// Colisão com bordas
				if (x < 0 || x > window.innerWidth - 20) vx *= -1;
				if (y < 0 || y > window.innerHeight - 20) vy *= -1;

				return { ...c, x, y, vx, vy };
			});

			// Atualiza a tela
			requestAnimationFrame(update);
		}

		// Começa a animação
		update();
	});
</script>

<svelte:head>
	<title>Sobre</title>
	<meta name="description" content="About this app" />
</svelte:head>

<div class="text-column">
	<h1>Sobre</h1>
</div>

<section class="ascii-art">
	{#each characters as { char, x, y, id }}
		<span class="character" style="transform: translate({x}px, {y}px);" key={id}>{char}</span>
	{/each}
</section>

<style>
	.text-column {
		position: relative;
		z-index: 1;
	}

	.ascii-art {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100vh;
		overflow: hidden;
		pointer-events: none;
	}

	.character {
		position: absolute;
		color: #ff4757;
		font-size: 20px;
		white-space: pre; /* Preserva os espaços em branco */
	}
</style>
