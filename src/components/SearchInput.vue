<template>
  		<input id='search' name="search" autocomplete="off" :value="value" :class="{dark}" @input="handleChange">
</template>

<script>
	export default {
  		name: 'SearchInput',
		props: {
			value: {
				type: String,
				required: true,
			},
			dark:{
				type: Boolean,
				default: false,
			},
		},
		methods:{
			handleChange(e){
				this.$emit('input', e.target.value);
			},
		},
	};
</script>

<style lang="scss" scoped>

	input{
		margin-top: 50px;
		display: flex;
		width: 250px;
		font-family: 'Montserrat', sans-serif;
		height: 30px;
		border: 0;
		border-bottom: 1px solid #FFF;
		background: none;
		color: #FFF;
		text-align: center;
		font-size: 16px;
		@media (min-width: 1024px){
			font-weight: 500;
		}
	}
	input:focus{
		outline: none;
	}
	.dark{
		color: black;
		border-bottom-color: #1E3D4A;
	}
</style>
