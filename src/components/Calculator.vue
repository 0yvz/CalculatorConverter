<template>
	<section class="calculator-advanced">
		<div class="calculator-advanced__output">
			{{ showingResult ? currentResult : currentInput }}
		</div>

		<div class="calculator-advanced__input">
			<div class="calculator-advanced__digits">
				<button @click="clearResult" class="calculator-advanced__button calculator-advanced__clear">C</button>
				<button @click="handleDigitInput(n)" class="calculator-advanced__button calculator-advanced__digit" v-for="n in 9">{{ n }}</button>
				<button @click="handleDigitInput(0)" class="calculator-advanced__button calculator-advanced__digit calculator-advanced__zero">0</button>
				<button @click="handleDigitInput('.')" class="calculator-advanced__button">,</button>
			</div>
			
			<div class="calculator-advanced__operators">
				<button @click="handleOperatorInput('/')" class="calculator-advanced__button calculator-advanced__operator">/</button>
				<button @click="handleOperatorInput('*')" class="calculator-advanced__button calculator-advanced__operator">*</button>
				<button @click="handleOperatorInput('-')" class="calculator-advanced__button calculator-advanced__operator">-</button>
				<button @click="handleOperatorInput('+')" class="calculator-advanced__button calculator-advanced__operator">+</button>
				<button @click="handleEqualsInput" class="calculator-advanced__button">=</button>
			</div>
		</div>


	</section>
</template>

<script>
	export default {
		data() {
			return {
				currentResult: 0,
				currentInput: '',
				currentOperator: null,
				showingResult: false,
			}
		},

		created() {
			window.addEventListener('keyup', this.handleKeyup);
		},
		
		computed: {
			currentInputAsNumber() {
				return Number(this.currentInput)
			},
		},

		methods: {
			calculateResult() {
				switch(this.currentOperator) {
					case '+':
						this.currentResult += this.currentInputAsNumber;
						break;
					case '-':
						this.currentResult -= this.currentInputAsNumber;
						break;
					case '/':
						this.currentResult /= this.currentInputAsNumber;
						break;
					case '*':
						this.currentResult *= this.currentInputAsNumber;
						break;
					default:
						this.currentResult = this.currentInputAsNumber;
				}
			},

			clearResult() {
				this.currentResult = 0;
				this.currentInput = '';
				this.currentOperator = null;
				this.showingResult = false;
			},
			
			handleOperatorInput(operator) {
				this.calculateResult();
				this.currentOperator = operator;
				this.currentInput = '';
				this.showingResult = true;
			},

			handleDigitInput(digit) {
				this.currentInput += digit;
				this.showingResult = false;
			},
			
			handleEqualsInput() {
				this.calculateResult();
				this.showingResult = true;
			},

			handleKeyup(event) {
				switch(event.key) {
					case '0':
					case '1':
					case '2':
					case '3':
					case '4':
					case '5':
					case '6':
					case '7':
					case '8':
					case '9':
						this.handleDigitInput(event.key)
						break;
					case '+':
					case '-':
					case '/':
					case '*':
						this.handleOperatorInput(event.key)
						break;
					case '.':
					case ',':
						this.handleDigitInput('.')
						break;
					case '=':
					case 'Enter':
						this.handleEqualsInput()
						break;
					case 'Escape':
					case 'Backspace':
						this.clearResult()
						break;
				}
			}
		}
	}
</script>

<style>
	.calculator-advanced {
		--background: #D1D8EC;
		--secondary: lightgray;
		--gap: 0.5em;
		--font-size-large: 3em;
		--font-size-medium: 1.5em;
	}
	
	body {
		color: rgba(114, 138, 183, 1);		
		background: #D1D8EC;
	}

	button {
		border-width: 0.2px;
		border-color: #D1D8EC;
	}

	.calculator-advanced {
		position: relative;
		margin: 10px;
		display: flex;
		top: 100px;
		left: 10%;
		transform: translateY(-50%), translateX(-50%);
		flex-flow: column nowrap;
		width: 20em;
		height: 35em;
		padding: 1em;
		-webkit-border-radius: 50px;
		border-radius: 15px;
		background: #D1D8EC;
		-webkit-box-shadow: 12px 12px 24px #b2b8c9, -12px -12px 24px #f0f8ff;
		box-shadow: 12px 12px 24px #b2b8c9, -12px -12px 24px #f0f8ffd1;
		font-family: "Courier New";
	}


	.calculator-advanced__output {
		font-size: 3em;
		width: 100%;
		min-height: 3em;
		background: #D1D8EC;
		box-shadow: inset -1px -1px 1px rgba(255, 255, 255, 0.7), inset 1.5px 1.5px 1px rgba(174, 174, 192, 0.2);
		border-radius: 5px;
		margin-bottom: 0.5em;
		overflow: hidden;
		text-overflow: ellipsis;
		white-space: nowrap;
	}

	.calculator-advanced__input {
		display: flex;
		gap: var(--gap);
		height: 100%;
	}

	.calculator-advanced__digits {
		display: grid;
		width: 80%;
		grid-template-columns: repeat(3, 1fr);
		gap: var(--gap);
	}

	.calculator-advanced__operators {
		display: flex;
		height: 100%;
		width: 20%;
		flex-flow: column nowrap;
		column-gap: 0.5em;
		row-gap: 0.5em;
	}
	
	.calculator-advanced__button {
		font-size: 1.5em;
		color: #7488c0;
		width: 100%;
		height: 100%;
		border-radius: 5px;
		background: #D1D8EC;
		-webkit-box-shadow: 6px 6px 12px #b2b8c974, -6px -6px 12px #f0f8ff89;
		box-shadow: 6px 6px 12px #b2b8c974, -6px -6px 12px #f0f8ff89;
		padding: 0.5em;
	}

	.calculator-advanced__button:hover {
		box-shadow: inset -1px -1px 1px rgba(255, 255, 255, 0.7), inset 1.5px 1.5px 1px rgba(174, 174, 192, 0.2);
		border-radius: 5px;
	}

	.calculator-advanced__button:active {
		box-shadow: inset -1px -1px 1px rgba(255, 255, 255, 0.7), inset 1.5px 1.5px 1px rgba(174, 174, 192, 0.2);
		border-radius: 5px;
	}

	.calculator-advanced__zero {
		grid-column: span 2;
	}

	.calculator-advanced__clear {
		grid-column: span 3;
	}
</style>