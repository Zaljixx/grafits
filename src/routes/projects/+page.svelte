<script>
	import { flip } from 'svelte/animate';

	export let images = [
		{
			id: '1',
			path: 'src/lib/assets/_STA3399_fotoAnsisStarks.png'
		},
		{
			id: '2',
			path: 'src/lib/assets/_STA3615_fotoAnsisStarks.png'
		},
		{
			id: '3',
			path: 'src/lib/assets/_STA3771_fotoAnsisStarks.png'
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
</script>

<div class="content-main">
	<div class="header">
		<div class="logo-container">
			<img class="small-logo" src="src/lib/assets/Logo_Dark_Grey_2B2D2C.svg" alt="" />
			
			
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
			<button id="left" on:click={rotateLeft}>
				<slot name="left-control">
					<svg width="39px" height="110px" id="svg8" transform={`scale(${controlScale})`}>
						<g id="layer1" transform="translate(-65.605611,-95.36949)">
							<path
								style={`fill:none;stroke:${controlColor};stroke-width:9.865;stroke-linecap:round;stroke-linejoin:bevel;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1`}
								d="m 99.785711,100.30199 -23.346628,37.07648 c -7.853858,12.81098 -7.88205,12.81098 0,24.78902 l 23.346628,37.94647"
								id="path1412"
							/>
						</g>
					</svg>
				</slot>
			</button>
			<button id="right" on:click={rotateRight}>
				<slot name="right-control">
					<svg
						width="39px"
						height="110px"
						id="svg8"
						transform={`rotate(180) scale(${controlScale})`}
					>
						<g id="layer1" transform="translate(-65.605611,-95.36949)">
							<path
								style={`fill:none;stroke:${controlColor};stroke-width:9.865;stroke-linecap:round;stroke-linejoin:bevel;stroke-miterlimit:4;stroke-dasharray:none;stroke-opacity:1`}
								d="m 99.785711,100.30199 -23.346628,37.07648 c -7.853858,12.81098 -7.88205,12.81098 0,24.78902 l 23.346628,37.94647"
								id="path1412"
							/>
						</g>
					</svg>
				</slot>
			</button>
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

		<img style="width: 95%;" src="src/lib/assets/_STA3113_fotoAnsisStarks_1920x1280.png" alt="" />
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

	button {
		position: absolute;
		top: 50%;
		transform: translateY(-50%);
		display: flex;
		align-items: center;
		justify-content: center;
		background: grey;
		border: none;
		width: 90px;
		height: 90px;
		opacity: 0.7;
		border-radius: 50%;
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
