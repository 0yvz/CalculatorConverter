<template>
		<section class="lenghtConverter">
			Feet to Cm
			<input class="lenghtConverter__input" type="number" placeholder="ft" v-model="valueFeet"/>
			<div class="lenghtConverter__output">{{ valueCm }}CM</div>
		</section>
</template>

<script>
	export default {
		data() {
			return {
				valueFeet: 1,
			}
		},

		computed: {
			valueCm() {
				return (this.valueFeet * 30.48);
			}
		}
	}
</script>

<style>

	.lenghtConverter {
		position: absolute;
		margin: 10px;
		display: flex;
		top: 100px;
		left: 55%;
		flex-flow: column nowrap;
		width: 15em;
		height: 5em;
		padding: 2em;
		-webkit-border-radius: 50px;
		border-radius: 15px;
		background: #D1D8EC;
		-webkit-box-shadow: 12px 12px 24px #b2b8c9, -12px -12px 24px #f0f8ffc7;
		box-shadow: 12px 12px 24px #b2b8c9, -12px -12px 24px #f0f8ffb3;
		font-family: "Courier New";
	}

	.lenghtConverter__input {
		background: #D1D8EC;
		box-shadow: inset -1px -1px 1px rgba(255, 255, 255, 0.7), inset 1.5px 1.5px 1px rgba(174, 174, 192, 0.2);
		border-radius: 5px;
		padding: 10px;
	}

</style>