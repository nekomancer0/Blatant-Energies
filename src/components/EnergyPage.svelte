<script lang="ts">
	import { onMount } from 'svelte';

	onMount(() => {
		let allA = document.querySelectorAll('a');

		for (let a of allA) {
			a.addEventListener('click', (ev) => {
				ev.preventDefault();
			});
		}

		let container = document.querySelector('div')!;

		let player2 = container.querySelector('.player-2')!;

		let value2 = player2.querySelector<HTMLParagraphElement>('.value')!;
		let addBtn2 = player2.querySelector<HTMLLinkElement>('.add')!;
		let removeBtn2 = player2.querySelector<HTMLLinkElement>('.remove')!;

		value2.classList.add('animate__animated');
		addBtn2.addEventListener('click', (ev) => {
			let val = parseInt(value2.textContent!) + 1;

			value2.textContent = val.toString();

			value2.classList.add('animate__bounceIn');

			setTimeout(() => {
				value2.classList.remove('animate__bounceIn');
			}, 800);
		});

		removeBtn2.addEventListener('click', (ev) => {
			let val = parseInt(value2.textContent!) - 1;

			value2.textContent = val.toString();

			value2.classList.add('animate__bounceIn');

			setTimeout(() => {
				value2.classList.remove('animate__bounceIn');
			}, 800);
		});

		let player = container.querySelector('.player-1')!;

		let value = player.querySelector<HTMLParagraphElement>('.value')!;
		let addBtn = player.querySelector<HTMLLinkElement>('.add')!;
		let removeBtn = player.querySelector<HTMLLinkElement>('.remove')!;

		value.classList.add('animate__animated');

		addBtn.addEventListener('click', (ev) => {
			let val = parseInt(value.textContent!) + 1;

			value.textContent = val.toString();

			value.classList.add('animate__bounceIn');

			setTimeout(() => {
				value.classList.remove('animate__bounceIn');
			}, 800);
		});

		removeBtn.addEventListener('click', (ev) => {
			let val = parseInt(value.textContent!) - 1;

			value.textContent = val.toString();

			value.classList.add('animate__bounceIn');

			setTimeout(() => {
				value.classList.remove('animate__bounceIn');
			}, 800);
		});
	});
</script>

<div class="container">
	<div class="player player-1">
		<input type="text" placeholder="Player 1" />

		<div class="counter">
			<p class="value">15</p>

			<div class="options">
				<a href="/" class="add">+1</a>
				<a href="/" class="remove">-1</a>
			</div>
		</div>
	</div>

	<div class="player player-2">
		<input type="text" placeholder="Player 2" />

		<div class="counter">
			<p class="value">15</p>

			<div class="options">
				<a href="/" class="add">+1</a>
				<a href="/" class="remove">-1</a>
			</div>
		</div>
	</div>
</div>

<style lang="scss">
	:global(body, html) {
		margin: 0;
		padding: 0;
		font-family: sans-serif;
	}

	a {
		text-decoration-line: none;
		color: white;
		opacity: 0.8;
	}

	.container {
		display: flex;
		width: 100vw;
		height: 100vh;
		justify-content: center;
		text-align: center;

		.player {
			width: 50%;

			input {
				border: 0;
				outline: 0;
				margin-top: 20px;
				padding-bottom: 5px;
				border-bottom: 1px solid white;
				background-color: transparent;
				text-align: center;
				color: white;
			}

			input::placeholder {
				color: white;
				opacity: 0.7;
			}

			.value {
				font-size: 7rem;
				color: white;
			}
		}

		.counter {
			display: flex;
			flex-direction: column;
			align-items: center;
			justify-content: center;

			height: 90vh;

			.options {
				display: flex;
				justify-content: space-around;
				width: 20%;
			}
		}

		.player-1 {
			background-color: rgb(211, 60, 60);
		}

		.player-2 {
			background-color: rgb(60, 125, 211);
		}
	}
</style>
