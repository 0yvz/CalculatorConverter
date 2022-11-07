<template>
 <Calculator/>
 <ConverterLenght/>
 <ConverterTemperature/>
 <ConverterWeight/>
</template>

<script>
	import Calculator from '../components/Calculator.vue';
	import ConverterLenght from '../components/ConverterLenght.vue';
	import ConverterTemperature from '../components/ConverterTemperature.vue';
	import ConverterWeight from '../components/ConverterWeight.vue'

	export default {
		components: {
    Calculator,
    ConverterLenght,
    ConverterTemperature,
	 ConverterWeight
}
	}
</script>

<style>
	/* @import 'style.css'; */
</style>