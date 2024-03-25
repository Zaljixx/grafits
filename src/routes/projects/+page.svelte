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
	export let imageWidth = '33%';
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
		window.location.href = '/#page-content';
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
	style=" margin-left: 32px;
margin-top: 32px; display: flex;"
>
	<div style="width: 33%;">
		<div id="carousel-container">
			<div id="carousel-images">
				{#each images as image (image.id)}
					<img
						src={image.path}
						alt={image.id}
						id={image.id}
						style={`width:${imageWidth}; height: 60vh`}
						animate:flip={{ duration: speed }}
					/>
				{/each}
			</div>
			<!-- svelte-ignore a11y-no-static-element-interactions -->
			<!-- svelte-ignore a11y-click-events-have-key-events -->
			<div on:click={rotateRight} class="left-circle"></div>
			<!-- svelte-ignore a11y-no-static-element-interactions -->
			<!-- svelte-ignore a11y-click-events-have-key-events -->
			<div on:click={rotateRight} class="right-circle"></div>
			<!-- svelte-ignore a11y-no-static-element-interactions -->
			<!-- svelte-ignore a11y-click-events-have-key-events -->
			<svg
				style="position: absolute; top: 30.6vh;
				left: 4px; color: white"
				xmlns="http://www.w3.org/2000/svg"
				version="1.1"
				width="40"
				height="40"
				on:click={rotateRight}
			>
				<path
					d="M24.5 11.5 L16.5 19.5 L24.5 27.5"
					stroke-linejoin="round"
					stroke-linecap="round"
					style="fill:none; stroke:#ffffff; stroke-width:3px"
				></path>
			</svg>
			<!-- svelte-ignore a11y-no-static-element-interactions -->
			<!-- svelte-ignore a11y-click-events-have-key-events -->
			<svg
				style="position: absolute; top: 30.6vh;
				right: 4px; color: white"
				xmlns="http://www.w3.org/2000/svg"
				version="1.1"
				width="40"
				height="40"
				on:click={rotateRight}
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
				<p style="font-family: 'IBM Plex Sans', sans-serif; font-sise:12px; margin-bottom: 0px">
					Client
				</p>
				<p style="font-family: 'IBM Plex Sans', sans-serif; font-sise:12px; margin-top: 0px">
					MADARA Retail
				</p>

				<p style="font-family: 'IBM Plex Sans', sans-serif; font-sise:12px; margin-bottom: 0px">
					Interior design
				</p>

				<p style="font-family: 'IBM Plex Sans', sans-serif; font-sise:12px; margin-top: 0px">
					Anete Eglīte Marta Gaile
				</p>
			</div>
			<div>
				<p style="font-family: 'IBM Plex Sans', sans-serif; font-sise:12px; margin-bottom: 0px">
					Furniture
				</p>
				<p style="font-family: 'IBM Plex Sans', sans-serif; font-sise:12px; margin-top: 0px">
					Edgara Baloža galdniecība
				</p>
				<p style="font-family: 'IBM Plex Sans', sans-serif; font-sise:12px; margin-bottom: 0px">
					Plaster
				</p>
				<p style="font-family: 'IBM Plex Sans', sans-serif; font-sise:12px; margin-top: 0px">
					KOURASANIT Latvija, SIA
				</p>
				<p style="font-family: 'IBM Plex Sans', sans-serif; font-sise:12px; margin-bottom: 0px">
					Decors and free-standing display tables
				</p>
				<p style="font-family: 'IBM Plex Sans', sans-serif; font-sise:12px; margin-top: 0px">
					AD production, SIA
				</p>
				<p style="font-family: 'IBM Plex Sans', sans-serif; font-sise:12px; margin-bottom: 0px">
					Metal parts
				</p>
				<p style="font-family: 'IBM Plex Sans', sans-serif; font-sise:12px; margin-top: 0px">
					GP Services, SIA
				</p>
				<p style="font-family: 'IBM Plex Sans', sans-serif; font-sise:12px; margin-bottom: 0px">
					Advertising stands
				</p>
				<p style="font-family: 'IBM Plex Sans', sans-serif; font-sise:12px; margin-top: 0px">
					Colorart Media, SIA
				</p>
				<p style="font-family: 'IBM Plex Sans', sans-serif; font-sise:12px; margin-bottom: 0px">
					Lighting
				</p>
				<p style="font-family: 'IBM Plex Sans', sans-serif; font-sise:12px; margin-top: 0px">
					Cenuklubs.lv, SIA
				</p>
			</div>
		</div>
	</div>

	<div style=" margin-left: 50px">
		<p
			style="font-family: 'PlayFair', serif; font-size: 31px; margin-top: 0px; font-weight: 400; margin-bottom: 0px"
		>
			MADARA Organic Skincare
		</p>
		<p style="font-family: 'PlayFair', serif; margin-top: 0px">Riga, 2023</p>

		<p style="font-family: 'IBM Plex Sans', sans-serif; width: 42vw;">
			New concept for retail stores was created to engage with customers in a new way. Sandy
			textures for ceilings, walls and floors made by hands wraps the space to create a calming
			background for a new shopping experience gently drawing attention to MADARA products
		</p>

		<p style="font-family: 'IBM Plex Sans', sans-serif; width: 42vw; margin-bottom: 48px">
			Contrasting elements - puffy green tables - are introduced for promotions and a playful
			element, chanterelle, can be exchanged to go along the brand story.
		</p>

		<img style="height: 53vh;" src="/_STA3113_fotoAnsisStarks_1920x1280.png" alt="" />
	</div>
</div>
<div class="footer">
	<div class="info-link">
		<p
			style="
		font-weight: 400;
		color: #2B2D2C;
		font-size: 16px;"
		>
			Instagram
		</p>
		<p class="link">Say hello! <a>grafiits@gmail.com</a></p>
	</div>
	<div>
		<p
			style="
		font-weight: 400;
		color: #2B2D2C;
		font-size: 16px; margin-right: 32px"
		>
			2024
		</p>
	</div>
</div>

<style style="scss">
	@import './projects.scss';
</style>
