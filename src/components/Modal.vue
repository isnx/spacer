<template>
	<div class="outerWrapper">
		<div class="innerWrapper">
			<div class="photo">
				<img :src="photo">
			</div>
			<div class="description">
				<h2 class="title">{{title}}</h2>
				<p>
					{{description}}
				</p>
			</div>
		</div>
		<div class="close" @click="$emit('closeModal')"/>
	</div>
</template>

<script>
	export default {
  		name: 'Modal',
		props:{
			item:{
				type: Object,
				required: true,
			},
		},
		data(){
			return{
				photo: null,
				title: null,
				description: null,
			};
		},
		mounted(){
			this.photo = this.item.links[0].href;
			this.title = this.item.data[0].title;
			this.description = this.item.data[0].description.substring(0, 200);
		},
	};
</script>

<style lang="scss" scoped>
	/*eslint linebreak-style: ["error", "windows"]*/
	.outerWrapper{
		background: #F0F0F0;
		max-width: 70%;
		max-height: 70%;
		position: fixed;
		top: 0;
		left: 0;
		right: 0;
		bottom: 0;
		margin: auto;
		color: black;
		box-shadow: 0 30px 30px -10px rgba(0,0,0, .3);
	}
	
	.close{
		position: absolute;
		right: 0;
		top: 0;
		width: 30px;
		height: 30px;
		cursor: pointer;
		padding: 30px;
		
		&::before,
		&::after{
			position: absolute;
			top: 30px;
			right: 20px;
			content: '';
			width: 20px;
			height: 2px;
			background: black;
			display: block;
		}
		
		&::before{
			transform: rotate(45deg);
		}
		
		&:after{
			transform: rotate(315deg);
		}
	}
	.innerWrapper{
		display: flex;
		height: 100%;
		padding: 20px;
		justify-content: center;
		align-items: center;
		flex-direction: column;
		overflow: hidden;
		flex-direction: row;
	}
	
	.photo{
		overflow: hidden;
		max-width: 60%;
		max-height: 90%;
		margin-right: 10px;
		line-height: 100%;
		vertical-align: middle;
	}
	.photo img{
		max-width: 100%;
		max-height: 100%;
	}
	.description{
		width: 40%;
		text-align: center;
	}
	//TABLET
	@media(max-width: 1024px){
		.outerWrapper{
			background: #F0F0F0;
			max-width: 100%;
			max-height: 100%;
			position: fixed;
			margin: auto;
		}
		.innerWrapper{
			display: flex;
			flex-flow: wrap;
			height: 100%;
			padding: 20px;
			justify-content: center;
			align-items: center;
			overflow: hidden;
			flex-direction: row;			
		}
		.photo{
			min-width: 100%;
			max-height: 50%;
			text-align: center;
			
		}
		.photo img{
			max-width: 100%;
			max-height: 100%;
		}
		.description{
			margin-top: 10px;
			margin-bottom: auto;
			width: 100%;
			text-align: center;
		}
		h2{
			font-size: 36px;
		}
		p{
			font-size: 24px;
		}
	}
	//SMARTPHONE
	@media(max-width: 768px){
		h2{
			font-size: 20px;
		}
		p{
			font-size: 12px;
		}
	}
	@media (max-width: 812px) and (orientation: landscape){
		.innerWrapper{
			display: flex;
			flex-flow: row;
			flex-direction: row;
		}
		
		.photo{
			min-width: 50%;
			max-height: 100%;
			text-align: center;			
		}

		.description{
			min-width: 50%;
			height: 100%;
		}
		h2{
			margin-top: 20%;
			font-size: 20px;
		}
		p{
			font-size: 12px;
		}
	}
	
</style>