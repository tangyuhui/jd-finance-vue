<template>
	<div class="fund-page">
		<div class="wrap">
			<div class="cp-category">
				<div class="swiper-container category-swiper-container">
					<div class="swiper-wrapper">
						<div class="swiper-slide category-swiper-slide headItem" v-for="(item, index) in items" v-bind:style="{fontSize:currentPageIndex==index ? 20+ 'px' : 16 + 'px',fontWeight:currentPageIndex==index?'bold':'normal'}">
						   {{item.ct}}
						</div>
					</div>
				</div>
				<div class="detailLine"></div>
			</div>
			<div class="swiper-container card-swiper-container">
				<div class="swiper-wrapper">
					<div class="swiper-slide card-swiper-slide" v-for="(item, index) in items">
						<div class="scroll-item" v-bind:style="itemStyle" :class="{swiperContain: currentPageIndex !== index}" >
							<div class="item-content">
								<h2 class="item-name f37 orange bold">
				  	 			 	{{item.ct}}
				  	 			 </h2>
								<p class="f14 lightGrey mt-10">{{item.pn}}</p>
								<p class="percent dinBold">{{item.rate}}<span class="f35">%</span></p>
								<p class="lightGrey f14">近7日年化(浮动)</p>
							</div>
							<div class="lr-row clear">
								<div class="column left center">
									<p class="f14 lightGrey">风险等级</p>
									<p class="f20 mt-5">{{item.rg}}</p>
								</div>
								<div class="column right center">
									<p class="f14 lightGrey">理财期限</p>
									<p class="f20 mt-5">{{item.dl}}</p>
								</div>
								<div class="divide-line"></div>
							</div>
							<button class="btn">
				  	 		 	立即赚钱
				  	 		  </button>
							<p class="lightGrey center">7日年化收益率(近3个月){{item.sr}}</p>
						</div>
					</div>
				</div>
				<!-- 如果需要分页器 -->
				<div class="swiper-pagination"></div>
			</div>
		</div>
	</div>
</template>

<script>
	import Swiper from 'src/plugins/swiper-4.2.0.min.js'
	import 'src/style/swiper-4.2.0.min.css'

	export default {
		data() {
			let width = document.documentElement.clientWidth;
			let height = document.documentElement.clientHeight;
			return {
				currentPageIndex:0,
				items:[{
					ct:'天天赚',
					pn:'泰达宏利活期友货币A',
					rate:'6.6800',
					rg:'低',
					dl:'灵活存取',
					sr:'2.1820% -6.7300%'
					
				},
				{
					ct:'月月赚',
					pn:'泰达宏利活期友货币A',
					rate:'6.6800',
					rg:'低',
					dl:'灵活存取',
					sr:'2.1820% -6.7300%'
					
				}],
				itemStyle: {
					width: width * 0.85 + 'px',
					height: height * 0.7 + 'px',
				}
			}
		},
		mounted() {
          this._initSwiper();
		},
		components: {

		},
		computed: {

		},
		methods: {
               _initSwiper(){
               	let self = this;
               	let navSwiper = new Swiper('.category-swiper-container',{
               	     direction: 'horizontal',
               	     slidesPerView: 'auto',
               		 centeredSlides: true,
               		 spaceBetween: 10
               	})
               	let cardSwiper = new Swiper('.card-swiper-container', {
				    direction: 'horizontal',
				    slidesPerView: 'auto',
				    spaceBetween: 2,
				    centeredSlides: true,
				    on:{ slideChangeTransitionStart:function(){
				      	self.currentPageIndex = this.activeIndex;
				      }} ,
				    loop: false,
				    // 如果需要分页器
				    pagination: {
				      el: '.swiper-pagination',
				    },
				    
				    // 如果需要前进后退按钮
				    navigation: {
				      nextEl: '.swiper-button-next',
				      prevEl: '.swiper-button-prev',
				    },
				    
				    // 如果需要滚动条
				    scrollbar: {
				      el: '.swiper-scrollbar',
				    },
				  })  
				  navSwiper.controller.control = cardSwiper;
                cardSwiper.controller.control = navSwiper;

               }
		},
		watch: {

		}
	}
</script>

<style lang="scss" scoped>
	@import 'src/style/mixin';
	.fund-page {
		position: absolute;
		left: 0;
		right: 0;
		top: 0;
		bottom: 0;
		overflow: hidden;
	}
	.cp-category{
		 padding-top:20px;
	}
	.headItem{
	 font-size: 16px;
	 text-align: center;
	 float: left;
	 color: #333;
	 line-height: 30px
	}
	.detailLine{
	    position: relative;
	    width: 40px;
	    height: 3px;
	    margin: auto;
	    margin-top: 5px;
	    background-color: #333333;
	    border-radius: 3px;
	}
	.category-swiper-slide{
		width:125px;
	}
	.card-swiper-slide{
		width:85%;
	}
	.wrap {
		width: 100%;
		height: 100%;
		background: url('./img/bg.jpg') no-repeat center center;
		background-size: cover;
	}
	
	.scroll-item {
		width:85px;
		background-color: #fff;
		margin: 50px auto;
		margin-right: 20px;
		border-radius: 5px;
		box-shadow: 0px 15px 20px 0px rgba(0, 33, 104, 0.6);
		transition: all 0.2s;
	}
	
	.item-content {
		padding: 44px 0 44px 44px;
	}
	.percent {
		font-size: 65px;
		margin-top: 6px;
		background-image: -webkit-gradient(linear, 0 0, 0 bottom, from(#ff8808), to(#ff2e0c));
		-webkit-background-clip: text;
		-webkit-text-fill-color: transparent;
		color: #ff5a17;
		text-shadow: 0 0 0, 2px 6px 7px rgba(245, 47, 62, 0.2)
	}
	
	.lr-row {
		position: relative;
		.divide-line {
			position: absolute;
			width: 1px;
			height: 32px;
			left: 0;
			margin: auto;
			top: 50%;
			margin-top: -16px;
			right: 0;
			background: #f0f0f0;
		}
		.column {
			width: 50%;
		}
	}
	
	.btn {
		position: relative;
		width: 90%;
		margin: 10px auto;
		background: #2298FF;
		color: #fff;
		height: 72px;
		display: block;
		font-size: 18px;
	}
	
	.swiperContain {
		-webkit-transform: scale(0.92);
		-moz-transform: scale(0.92);
		-ms-transform: scale(0.92);
		transform: scale(0.92);
		transform-origin: center;
		overflow: hidden;
	}
</style>