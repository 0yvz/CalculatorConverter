<template>
		<section class="converter">
			Celcius to Farenheit
			<input class="converter__input" type="number" placeholder="℃" v-model="valueCelcius"/>
			<div class="converter__output">{{ valueFarenheit }}F</div>
		</section>
</template>

<script>
	export default {
		data() {
			return {
				valueCelcius: 10,
			}
		},

		computed: {
			valueFarenheit() {
				return (this.valueCelcius * 1.8) + 32;
			}
		}
	}
</script>

<style>
	.converter {
		position: absolute;
		margin: 10px;
		display: flex;
		top: 300px;
		left: 55%;
		flex-flow: column nowrap;
		width: 15em;
		height: auto;
		padding: 2em;
		-webkit-border-radius: 50px;
		border-radius: 15px;
		background: #D1D8EC;
		-webkit-box-shadow: 12px 12px 24px #b2b8c9, -12px -12px 24px #f0f8ffc7;
		box-shadow: 12px 12px 24px #b2b8c9, -12px -12px 24px #f0f8ffa3;
		font-family: "Courier New";
	}

	input {
		border: 0;
		color: inherit;
	}

	.converter__input {
		background: #D1D8EC;
		box-shadow: inset -1px -1px 1px rgba(255, 255, 255, 0.7), inset 1.5px 1.5px 1px rgba(174, 174, 192, 0.2);
		border-radius: 5px;
		padding: 10px;
		margin: 5px;
	}

	.converter__output {
		margin: 5px;
	}
</style>