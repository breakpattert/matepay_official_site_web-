<template>
	<div class="main-page">
		<div class="left"
			 :class="showAbout ? 'animate-slider' : ''">
			<div class="left-main">
				<a style="color: #686060;">分享：</a>
				<div style="width:20px;height:20px;margin-left:6px;display: inline-block;"  @click="click()">
					
					<img src="../assets/gbRes_6.png" alt="" style="width:100%">
				</div>
				<div class="logo" style="width: 120px;box-sizing:border-box;background-size:cover; margin-top: 50px;">
					<img src="../assets/logo@2x.png" alt="" style="width:100%">
				</div>
			
				
				<transition-group 
					name="component-fade"
					mode="out-in"
					>
					<div v-show="!showAbout" key="describe" class="describe-wrap">
						<div class="describe">
							<swiper :options="desSwiperOpt" :not-next-tick="notNextTick" ref="desSwiper">
								<swiper-slide v-for="item in describes" :key="item.tit">
									<div class="tit">{{item.tit}}</div>
									<div class="des">{{item.des}}</div>
								</swiper-slide>
							  </swiper>
						</div>

						<div class="download" key="download">
							<!-- <a href="http://a.app.qq.com/o/simple.jsp?pkgname=cn.highing.hichat&g_f=991653"> -->
							<div class="ios download-box">
								<img src="../assets/apple.png">App Store
								<div class="qr-code">
									<img v-if="online" src="../assets/qr_code.png" alt="">
									<img v-else src="../assets/qr_code_down.png" alt="">
								</div>
							</div>
							<!-- </a> -->
							
							<!-- <a href="http://a.app.qq.com/o/simple.jsp?pkgname=cn.highing.hichat&g_f=991653"> -->
							<div class="android download-box">
								<img src="../assets/appbao.png">My App
								<div class="qr-code">
									<img v-if="online" src="../assets/qr_code.png" alt="">
									<img v-else src="../assets/qr_code_down.png" alt="">
								</div>
							</div>
							<!-- </a> -->
							
						</div>
					</div>

					<div class="aboutus-main" v-show="showAbout" key="about">
						<div class="about-tit" style="margin-top: 85px;">
							加入我们
						</div>
						<div class="about-des">
							运营、程序员等众多职位持续开放中，如果你感兴趣那就快快加入我们吧，我们在 <a :href="'mailto:' + mails.hr" target="_top">{{mails.hr}}</a> 等你，欢迎来看看哟！
						</div>

						<div class="about-tit">
							联系我们
						</div>
						<div class="about-des">
							电子邮箱：<a :href="'mailto:' + mails.contact" target="_top">{{mails.contact}}</a> 
						</div>
						<div class="about-des">
							联系电话：0571-28229863
						</div>
					</div>
				
					
				</transition-group >

				<!-- <transition 
					name="component-fade"
					mode="out-in"
					>
					<div class="aboutus-main" v-show="showAbout">
						<div class="about-tit" style="margin-top: 85px;">
							加入我们
						</div>
						<div class="about-des">
							运营、程序员等众多职位持续开放中，如果你感兴趣那就快快加入我们吧，我们在 <a :href="'mailto:' + mails.hr" target="_top">{{mails.hr}}</a> 等你，欢迎来看看哟！
						</div>

						<div class="about-tit">
							联系我们
						</div>
						<div class="about-des">
							电子邮箱：<a :href="'mailto:' + mails.contact" target="_top">{{mails.contact}}</a> 
						</div>
						<div class="about-des">
							联系电话：0571-28229863
						</div>
					</div>
				</transition> -->
				
			</div>
		</div><!-- 
	 --><div class="right">
			<div class="right-header" :class="showAbout ? 'right-header-about' : 'right-header-home'">
				<a class="a-home" @click="toggleAbout(false)">首页</a>   <span style="color:#fff">|</span>
				<a class="a-about" @click="toggleAbout(true)">关于我们</a>
			</div>

			<div class="phone">
				<div class="phone-page">
					<swiper :options="swiperOption" :not-next-tick="notNextTick" ref="phoneSwiper">
						<swiper-slide v-for="(item, index) in phonePage" :key="index">
							<img :src="phomeImg(index)" class="phone-img">
						</swiper-slide>
					</swiper>
				</div>
			</div>
		</div>
	</div>
</template>
<script>
	import { swiper, swiperSlide } from 'vue-awesome-swiper'
	export default {
		name: 'main-page',
		components: {
			swiperSlide,
			swiper
		},
		data(){
			return {
				online: false,
				mails: {
					hr: 'hr@matepay.cc',
					contact: 'matepay@matepay.cc'
				},
				describes: [{
					tit: '恋爱基金',
					des: '爱就是积少成多每一天'
				},{
					tit: '愿望清单',
					des: '一起实现我们共同的愿望'
				},{
					tit: '恋爱日记',
					des: '记下每一道爱的印记'
				}],
				phonePage: [{
					name: 'home.png',
					url: '../assets/home.png'
				},{
					name: 'wish.png',
					url: '../assets/wish.png'
				},{
					name: 'diary.png',
					url: '../assets/diary.png'
				}],
				showAbout: false,
				notNextTick: true,
				desSwiperOpt: {
					// onInit() {
					// 	console.log('onInit', this)
					// 	this.swiper = this.$refs.desSwiper.swiper;
					// 	console.log('swiper', this.swiper)
					// },
					onlyExternal: true,
					height: 'auto',
					loop : true,
					autoplay: 3000,
					direction : 'horizontal',
					grabCursor : true,
					setWrapperSize :true,
				},
		        swiperOption: {
	        	  onlyExternal: true,
		          // swiper optionss 所有的配置同swiper官方api配置
		          height: 'auto',
		          loop : true,
		          // autoplay: 3000,
		          direction : 'horizontal',
		          grabCursor : true,
		          setWrapperSize :true,
		          // autoHeight: true,
		          // 如果自行设计了插件，那么插件的一些配置相关参数，也应该出现在这个对象中，如下debugger
		          // debugger: true,
		          // swiper callbacks
		          // swiper的各种回调函数也可以出现在这个对象中，和swiper官方一样
		          // onTransitionStart(swiper){
		          //   console.log(swiper)
		          // },
		        }
			}
		},
		computed: {
	      swiper() {
	        return this.$refs.desSwiper.swiper
	      },
	      pswiper() {
	      	return this.$refs.phoneSwiper.swiper
	      }
	    },
	    methods: {
	    	toggleAbout(isShow){
	    		this.showAbout = !!isShow;
	    	},
	    	click(){
	    		   window.location.href='http://v.t.sina.com.cn/share/share.php';
                
            
	    	},
	    	      
                
               
            
	    	phomeImg(index){
	    		var item = this.phonePage[index];
	    		return 'http://matepay-oss.oss-cn-hangzhou.aliyuncs.com/marketing_site/aaets/' + item.name;
	    	}
	    },
	    mounted(){
	    	// this.swiper.slideTo(0, 1000, false)
	    	var desSwiper = this.swiper,
	    		phoneSwiper = this.pswiper;

	    	console.log('desSwiper', desSwiper)
	    	console.log('phoneSwiper', phoneSwiper)
	    	desSwiper.onTransitionStart = function desOnTransitionStart(){
	    		phoneSwiper.slideNext();
	    	}
	    	// desSwiper.onSlideChangeStart = function phoneOnSlideChangeStart(swiper){
	    	// 	// debugger;
	    	// }
	    	
	    	// console.log('phoneSwiper', phoneSwiper)
	    	// console.log('desSwiper' ,this.$refs.desSwiper)
	    }
	}
</script>
<style lang="scss">
	
	.main-page {
		position: relative;
		// height: 900px;
		height: 100vh;
		min-width: 1440px;
		.left {
			position: absolute;
			top: 0;
			left: 0;
			z-index: 10;
			// width: 800px;
			width: 56%;

			transition: width 1s;
			text-align: center;
			
			height: 100%;
			/*background-color: #red;*/
		background: linear-gradient(to bottom right, #fffff, #ffffff);
			/*box-shadow: 5px 0px 29px #ffff;
			// box-shadow: 14px 0px 35px rgba(234, 79, 82, .5);
			box-shadow: 5px 0px 29px rgba(234, 79, 82, 0.5);*/

			.left-main {
				height: 100%;
				text-align: left;
				min-width: 380px;
				// margin-top: 35px;
				padding-top: 3.88vh;
				box-sizing: border-box;
				margin-left: 20%;
		
			}
		}

		.right {
			overflow: hidden;
			position: relative;

			margin-left: 800px;
			text-align: center;

			height: 100%;
			// width: 44%;
			background-color: #43ddfb;

			.right-header {
				position: absolute;
				left: 50%;
				z-index: 100;

				margin-top: 42px;
				margin-top: 5.5vh;
				margin-bottom: 110px;
				margin-left: -71px;
				.a-home {
					margin-right: 22px;
				}
				.a-about {
					margin-left: 16px;
				}
				a {
					font-size: 16px;
					text-decoration: none;
					color: #fff;
					cursor: pointer;
				}
			}
			.right-header.right-header-home .a-home,
			.right-header.right-header-about .a-about {
				font-weight: bolder;
			}
			.right-header.right-header-about {
				color: #fff;
				a {
					color: #fff;
				}
			}
			.phone {
				position: relative;

				margin: 0 auto;
				margin-top: 150px;
				margin-top: 12.666vh;
				width: 353px;
				height: 664px;
				background: url(../assets/phone1.png) no-repeat;

				.phone-page {
					position: relative;
					top: 79px;
					left: 26px;
					width: 264px;
					height: 469px;
					.phone-img {
						width: 100%
					}
				}
			}
		}
	}
	.describe-wrap {
		margin-top: 300px;
		margin-top: 15.33vh;
	}
	.describe {
		// margin-top: 300px;
		display: inline-block;
		color: #fff;
		width: 350px;
		overflow: hidden;
		.tit {
			margin-bottom: 20px;
			font-size: 36px;
			font-weight: 400;
			color:#686060;
		}
		.des {
			font-size: 28px;
			font-weight: 100;
			color:#686060;
		}
	}
	.download {
		margin-top: 97px;
		margin-top: 10.88vh;
		.download-box {
			position: relative;
			display: inline-block;
			width: 186px;
			height: 60px;
			line-height: 60px;
			border-radius: 93px;
			text-align: center;
			cursor: pointer;
			> img {
				height: 23px;
				width: 23px;

				vertical-align: middle;
				margin-bottom: 5px;
				margin-right: 8px;
			}
			.qr-code {
				display: none;
				position: absolute;
				top: 60px;
				left: 0;

				transition: opacity 2s;
				opacity: 0;
			}
			&:hover .qr-code {
				display: block;
				opacity: 1;
			}
		}
		.ios {
			color: #fff;
			margin-right: 12px;
			background-color: #43ddfb;
		}
		.android {
			background-color: #ff5c6f;
			color: #fff;
		}
	}
	.aboutus-main {
		color: #fff;
		text-align: left;
		.about-tit {
			margin-top: 55px;
			margin-bottom: 20px;
			font-size: 24px;
			font-weight: 400;
		}
		.about-des {
			font-size: 18px;
			line-height: 32px;
			font-weight: 100;
			a {
				text-decoration: none;
				color: #fff;
			}
		}
	}
	
	.inline {
		display: inline-block;
	}

	.main-page .animate-slider {
		background:#43ddfb;
		// animation-duration: 2s;
		// animation-fill-mode: both;
		// animation-name: slider;
		width: 100%;
		// width: 75%;
	}
	@keyframes slider {
		0% {
			width: 56%;
		}
		100% {
			width: 100%;
		}
	}

	.component-fade-enter-active, .component-fade-leave-active {
	  transition: opacity .3s ease;
	}
	.component-fade-enter, .component-fade-leave-to {
	  opacity: 0;
	}

	.swiper-slide {
		overflow: hidden;
	}

</style>
