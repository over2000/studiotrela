<script>
	import Counter from './Counter.svelte';
	import welcome from '$lib/images/trelo.png';
	import welcome_fallback from '$lib/images/trelo.png';
	import backgroundVideo from '$lib/video/video.mp4'; // Importe o vídeo
</script>

<svelte:head>
	<title>Ⲧ ℛ ᙓ ᥨ ລ</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<div class="video-background">
	<video autoplay muted loop playsinline class="background-video">
		<source src={backgroundVideo} type="video/mp4" />
		Seu navegador não suporta a tag de vídeo.
	</video>
	
	<section class="content">
		<h1>
			<span class="welcome">
				<picture>
					<source srcset={welcome} type="image/webp" />
					<img src={welcome_fallback} alt="Welcome" />
				</picture>
			</span>
		</h1>
	</section>

	<div class="falling-characters">
		<span class="character">💋ྀིྀི</span>
		<span class="character">Ⲧ ℛ ᙓ ᥨ ລ</span>
		<span class="character">🍒</span>
		
		<!-- Glitches adicionais -->
		<span class="glitch">⋆</span>
		<span class="glitch">❦</span>
		<span class="glitch">⋆</span>
		<span class="glitch">♱</span>
		<span class="glitch">♡ྀི</span>
		<span class="glitch">⋆</span>
	</div>
</div>

<style>
	.video-background {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		overflow: hidden;
		z-index: -1;
	}

	.background-video {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		object-fit: cover;
	}

	.content {
		display: flex;
		justify-content: center;
		align-items: center;
		width: 100%;
		height: 100vh;
		position: relative;
		z-index: 1;
	}

	h1 {
		width: auto;
	}

	.welcome {
		display: block;
		width: auto;
	}

	.welcome img {
		width: 100%;
		height: auto;
		display: block;
	}

	.falling-characters {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		pointer-events: none;
		overflow: hidden;
		z-index: 2;
	}

	.character {
		position: absolute;
		color: pink;
		font-size: 29px; /* Tamanho dos caracteres reduzido */
		animation: fall 5s infinite linear;
		opacity: 0.8;
	}

	.glitch {
		position: absolute;
		color: pink;
		font-size: 58px;
		animation: glitch 3s infinite ease-in-out;
		opacity: 0.8;
	}

	@keyframes fall {
		0% {
			transform: translateY(-100%);
			opacity: 0;
		}
		10% {
			opacity: 0.8;
		}
		100% {
			transform: translateY(100vh);
			opacity: 0;
		}
	}

	@keyframes glitch {
		0%, 100% {
			transform: translate(0, 0) skew(0deg, 0deg);
			opacity: 0;
		}
		20% {
			transform: translate(-5px, 5px) skew(-5deg, 5deg);
			opacity: 0.8;
		}
		40% {
			transform: translate(5px, -5px) skew(5deg, -5deg);
			opacity: 0.5;
		}
		60% {
			transform: translate(-3px, 3px) skew(-3deg, 3deg);
			opacity: 0.7;
		}
		80% {
			transform: translate(3px, -3px) skew(3deg, -3deg);
			opacity: 0.9;
		}
	}

	/* Configurações de posição e variações de tempo para os caracteres */
	.character:nth-child(1) {
		left: 10%;
		animation-delay: 0s;
	}
	.character:nth-child(2) {
		left: 50%;
		animation-delay: 2s;
	}
	.character:nth-child(3) {
		left: 80%;
		animation-delay: 4s;
	}

	.glitch:nth-child(4) {
		left: 20%;
		top: 10%;
		animation-delay: 0.5s;
	}
	.glitch:nth-child(5) {
		left: 60%;
		top: 30%;
		animation-delay: 1.5s;
	}
	.glitch:nth-child(6) {
		left: 40%;
		top: 50%;
		animation-delay: 2.5s;
	}
	.glitch:nth-child(7) {
		left: 70%;
		top: 70%;
		animation-delay: 3.5s;
	}
	.glitch:nth-child(8) {
		left: 30%;
		top: 80%;
		animation-delay: 4.5s;
	}
	.glitch:nth-child(9) {
		left: 50%;
		top: 90%;
		animation-delay: 5.5s;
	}
</style>
