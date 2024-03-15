<script>
	import { ChevronLeftSolid } from 'flowbite-svelte-icons';
	import { flip } from 'svelte/animate';

	export let images = [
		{
			id: '1',
			path: '/_STA3399_fotoAnsisStarks.png'
		},
		{
			id: '2',
			path: '/_STA3615_fotoAnsisStarks.png'
		},
		{
			id: '3',
			path: '/_STA3771_fotoAnsisStarks.png'
		}
	];
	export let imageWidth = '31%';
	export let speed = 500;
	export let controlColor = 'white';
	export let controlScale = '0.5';

	// @ts-ignore
	const rotateLeft = (e) => {
		const transitioningImage = images[images.length - 1];
		// @ts-ignore
		document.getElementById(transitioningImage.id).style.opacity = 0;
		images = [images[images.length - 1], ...images.slice(0, images.length - 1)];
		// @ts-ignore
		setTimeout(() => (document.getElementById(transitioningImage.id).style.opacity = 1), speed);
	};

	// @ts-ignore
	const rotateRight = (e) => {
		const transitioningImage = images[0];
		// @ts-ignore
		document.getElementById(transitioningImage.id).style.opacity = 0;
		images = [...images.slice(1, images.length), images[0]];
		// @ts-ignore
		setTimeout(() => (document.getElementById(transitioningImage.id).style.opacity = 1), speed);
	};

	function goHome() {
		window.location.href = '/';
	}
</script>

<div>
	<div class="header">
		<div on:click={goHome} class="logo-container">
			<img class="small-logo" src="/Logo_Dark_Grey_2B2D2C.svg" alt="" />
		</div>

		<div>
			<ul class="navigation">
				<li><a href="about">About Us</a></li>
				<li><a href="projects">Projects</a></li>
			</ul>
		</div>
	</div>
</div>

<div
	style=" margin-left: 59px;
margin-top: 59px; display: flex;"
>
	<div style="width: 27%;">
		<div id="carousel-container">
			<div id="carousel-images">
				{#each images as image (image.id)}
					<img
						src={image.path}
						alt={image.id}
						id={image.id}
						style={`width:${imageWidth};`}
						animate:flip={{ duration: speed }}
					/>
				{/each}
			</div>
			<div class="left-circle"></div>
			<div class="right-circle"></div>
			<div class="left-arrow">
				<ChevronLeftSolid id="left" on:click={rotateLeft} style="color: white" size="xl" />
			</div>
			<!-- <div class="right-arrow">
				<ChevronRightSolid  id="right" on:click={rotateRight} style="color: white"   size="xl" />
			</div> -->
			<svg
				style="position: absolute; top:50%; right:0; color: white"
				xmlns="http://www.w3.org/2000/svg"
				version="1.1"
				width="40"
				height="40"
			>
				<path
					d="M16.5 11.5 L24.5 19.5 L16.5 27.5"
					stroke-linejoin="round"
					stroke-linecap="round"
					style="fill:none; stroke:#ffffff; stroke-width:3px"
				></path>
			</svg>
		</div>
		<div style="display: flex;">
			<div>
				<h3>Client</h3>
				<h3>MADARA Retail</h3>

				Interior design Anete Eglīte Marta Gaile
			</div>
			<div>
				<h3>Furniture</h3>
				<h3>Plaster KOURASANIT Latvija, SIA</h3>
				<h3>Decors and free-standing display tables AD production, SIA</h3>
				<h3>Metal parts GP Services, SIA</h3>
				<h3>Advertising stands Colorart Media, SIA</h3>

				<h3>Starks Lighting Cenuklubs.lv, SIA</h3>
			</div>
		</div>
	</div>

	<div style=" margin-left: 50px">
		<h1>MADARA Organic Skincare</h1>
		<h3>Riga, 2024</h3>

		<h3>
			New concept for retail stores was created to engage with customers in a new way. Sandy
			textures for ceilings, walls and floors made by hands wraps the space to create a calming
			background for a new shopping experience gently drawing attention to MADARA products.
			Contrasting elements - puffy green tables - are introduced for promotions and a playful
			element, chanterelle, can be exchanged to go along the brand story.
		</h3>

		<img style="width: 95%;" src="/_STA3113_fotoAnsisStarks_1920x1280.png" alt="" />
	</div>
</div>
<div class="footer">
	<div class="info-link">
		<p>Instagram</p>
		<p class="link">studio@grafiits.com</p>
	</div>
	<div><h4>2024</h4></div>
</div>

<style style="scss">
	@import './projects.scss';
	#carousel-container {
		width: 100%;
		height: 92vh;
		position: relative;
		display: flex;
		flex-direction: column;
		overflow-x: hidden;
	}
	#carousel-images {
		height: 700px;
		width: 100vw;
	}

	.left-arrow {
		position: absolute;
		top: 50%;
		width: 90px;
		height: 90px;
	}

	.left-circle {
		border: none;
		background-color: gray;
		position: absolute;
		top: 50%;
		width: 75px;
		height: 75px;
		opacity: 0.7;
		border-radius: 50%;
	}

	.right-circle {
		border: none;
		background-color: gray;
		position: absolute;
		top: 50%;
		right: 0;
		width: 75px;
		height: 75px;
		opacity: 0.7;
		border-radius: 50%;
	}

	.right-arrow {
		position: absolute;
		top: 50%;
		right: 0;
		border: none;
		width: 90px;
		height: 90px;
	}

	button:focus {
		outline: auto;
	}

	#left {
		left: 10px;
	}

	#right {
		right: 10px;
	}
</style>
