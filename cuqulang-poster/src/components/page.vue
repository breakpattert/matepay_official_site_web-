<template>
	<div class="page">
		<div class="log-img"></div>
		<!-- <img :src="imgUrl" class="poster-img"> -->
	</div>
</template>

<script>
	export default {
		name: 'page',
		props: {
			page: {
				type: Object,
				default: null
			}
		},
		data() {
			return {

			}
		},
		computed: {
			imgUrl: function(){
				return require('../assets/' + this.page.imgName)
			}
		}
	}
</script>

<style lang="scss">
	.page {
		position: relative;
		// height: 500px;  
		background-color: red;
		.log-img {
			position: absolute;
			top: 46px;
			right: 20px;

			background: url("../assets/scan.png") no-repeat;
			height: 100px;
			width: 100px;
		    transition: all 300ms ease-in-out;
			&:hover {
				width: 200px;
				height: 200px;
				background: url("../assets/qr_code.png") no-repeat;
			}
		}
		.poster-img {
			width: 100%;
			display: block;
		}
	}
	
</style>