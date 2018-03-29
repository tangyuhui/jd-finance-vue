<template>
	<div>
		<head-top signin-up='home'>
		</head-top>
		<div class="swiper-container">
			<div class="swiper-wrapper">
				<div class="swiper-slide" v-for="(item, index) in swiperImg" :key="index">
					<img :src="item" alt="" class="swiperImg">
				</div>
			</div>
			<div class="swiper-pagination"></div>
		</div>
		<div class="nav-container">
			<ul class="nav clear">
				<li>
					<figure>
						<img src="https://img12.360buyimg.com/jrpmobile/jfs/t3991/64/2521945388/12110/93c0139/58d1e462Ncf294123.png?width=132&height=132" class="icon" />
						<figcaption class="mt-5">
							优惠券
						</figcaption>
					</figure>
				</li>
				<li>
					<figure>
						<img src="https://img12.360buyimg.com/jrpmobile/jfs/t5590/252/875247023/17343/946aa72c/59224650N0f7ffc92.png?width=132&height=132" class="icon" />
						<figcaption class="mt-5">
							领红包
						</figcaption>
					</figure>
				</li>
				<li>
					<figure>
						<img src="https://img12.360buyimg.com/jrpmobile/jfs/t4393/329/2180608902/13217/c88c0cec/58ec9dcdN1534e2d7.png?width=132&height=132" class="icon" />
						<figcaption class="mt-5">
							抢钢镚
						</figcaption>
					</figure>
				</li>
				<li>
					<figure>
						<img src="https://img12.360buyimg.com/jrpmobile/jfs/t5488/298/1036263348/12073/b4f4de97/590ac8e8Ne9def22e.png?width=135&height=135" class="icon" />
						<figcaption class="mt-5">
							白条提额
						</figcaption>
					</figure>
				</li>
			</ul>
		</div>
		<div class="financial-recommend mt-10 content">
			<h2 class="bold f16 center row-title">-理财精选-</h2>
			<div class="flex row">
				<div class="column">
					<div class="f15 bold">
						<span class="bold">定期理财</span>
						<span class="tips">90天可质押</span>
					</div>
					<div class="rate-num f22 bold">5.50%</div>
					<div class="rate-title">历史年化结算利率</div>
				</div>
				<div class="column">
					<div class="f15 bold">
						<span class="bold">固收理财</span>
						<span class="tips">理财推荐</span>
					</div>
					<div class="rate-num f22 bold">5.80%</div>
					<div class="rate-title">综合年化收益率</div>
				</div>
			</div>
			<div class="flex row">
				<div class="column">
					<div class="f15 bold">
						<span class="bold">基智账户</span>
						<span class="tips">组合投资</span>
					</div>
					<div class="rate-num f22 bold">8%-10%</div>
					<div class="rate-title">止盈年化收益率</div>
				</div>
				<div class="column">
					<div class="f15 bold">
						<span class="bold">小白基金</span>
						<span class="tips">超短期</span>
					</div>
					<div class="rate-num f22 bold">5.00%</div>
					<div class="rate-title">7日年化收益率</div>
				</div>
			</div>
		</div>
		<div class="content mt-10">
			<h2 class="bold f16 center row-title">-众筹新品-</h2>
			<div class="zc-wrapper" ref="zcWrapper">
				<ul class="zc-list clear" ref="zcList">
					<li class="zc-item left" v-for="pic in zc.pics">
						<img :src="pic" width="125" height="157">
					</li>
				</ul>
			</div>
		</div>
	</div>
</template>

<script>
	import headTop from '../../components/header/head'
	import BScroll from 'better-scroll'
	import 'src/plugins/swiper.min.js'
	import 'src/style/swiper.min.css'

	export default {
		data() {
			return {
				swiperImg: [
					require('./img/01.jpg'),
					require('./img/02.jpg')
				],
				zc: {
					pics: [
						 'https://img12.360buyimg.com/jrpmobile/jfs/t19063/263/1067257870/16513/d7360e92/5ab85da9N8af17d57.jpg?width=335&height=421',
						  'https://img12.360buyimg.com/jrpmobile/jfs/t19063/263/1067257870/16513/d7360e92/5ab85da9N8af17d57.jpg?width=335&height=421',
						 'https://img12.360buyimg.com/jrpmobile/jfs/t19063/263/1067257870/16513/d7360e92/5ab85da9N8af17d57.jpg?width=335&height=421',
						  'https://img12.360buyimg.com/jrpmobile/jfs/t19063/263/1067257870/16513/d7360e92/5ab85da9N8af17d57.jpg?width=335&height=421'
					]
				}
			}
		},
		mounted() {
			this._init_zcxp();
		},
		components: {
			headTop
		},

		computed: {

		},
		methods: {
			//点击图标刷新页面
			reload() {
				window.location.reload();
			},
			_init_zcxp() {
				let picWidth = 125;
				let margin = 12;
				let leftMargin=16;
				let width = (picWidth + margin) * this.zc.pics.length + leftMargin
				this.$refs.zcList.style.width = width + 'px';
				this.$nextTick(() => {
					if(!this.zcScroll) {
						this.zcScroll = new BScroll(this.$refs.zcWrapper, {
							scrollX: true,
							eventPassthrough: 'vertical'
						});
					} else {
						this.zcScroll.refresh();
					}
				});
			}
		},
	}
</script>

<style lang="scss" scoped>
	@import '../../style/mixin';
	.swiper-container {
		margin-top: 60px;
		width: 100%;
		height: 160px;
	}
	
	.swiperImg {
		width: 100%;
		height: 160px;
	}
	
	.nav {
		padding: 20px 0 10px 0;
		background-color: #fff;
	}
	
	.nav>li {
		float: left;
		width: 25%;
		height: 100%;
		text-align: center;
		color: #666;
		font-size: 14px;
	}
	
	.icon {
		height: 45px;
		width: 45px;
	}
	
	.content {
		background-color: #fff;
	}
	
	.row-title {
		height: 56px;
		line-height: 56px;
	}
	
	.financial-recommend {
		.row {
			height: 109px;
		}
		.rate-num {
			margin-top: 8px;
			color: #FF5155;
		}
		.rate-title {
			height: 17px;
			line-height: 17px;
			color: #999;
		}
		.tips {
			border: 1px solid #FF5155;
			height: 17px;
			line-height: 17px;
			font-size: 11px;
			padding: 0 4px;
			color: #FF5155;
			position: relative;
			text-align: center
		}
	}
	
	.flex {
		display: flex;
		justify-content: space-between;
		.column {
			flex: auto;
			padding-left: 16px;
			text-align: left;
		}
	}
	
	.zc-wrapper {
		width: 100%;
		overflow: hidden;
	}
	.zc-item:first-child{
		margin-left: 16px;
	}
	.zc-item{
		margin-right:12px;
	}
</style>