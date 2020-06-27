<template>
	<view>
		<view class="page-section">
			<view class="page-row">
				<view class="city-select-box">
					<view class="city-select-button">
						{{currentCity}}
					</view>
					<image src="/static/arrow_down.png" class="city-select-image"></image>
				</view>
				<view class="search-box">
					<image src="/static/search.png" class="search-image"></image>
					<input class="search-input" placeholder="搜索商品" />
				</view>
			</view>
		</view>
		<view class="page-section">
			<special-banner :banner-list="bannerList" :swiper-config="swiperConfig" @tapButtonItem='tapButtonItem'>
			</special-banner>
		</view>
		<view class="page-section" style='align-items: center;justify-content: center;'>
			<view class="section-content">
				<view class="opt-area">
					<view class="opt-button" v-for="(item, index) in optList" :key='item.icon'>
						<image v-bind:src="item.icon" class="opt-icon"></image>
					</view>
				</view>
				<view class="notic-area">
					<image src='../../static/notice.png' class="notice-icon"></image>
					<scroll-view class="notice-list" scroll-y='true' :scroll-into-view="block" scroll-with-animation='true'
					 show-scrollbar='false'>
						<view class="notice-item" v-for="(item, index) in noticeList" :key='item.title' v-bind:id="'block' + index">
							{{item.title}}
						</view>
					</scroll-view>
				</view>
			</view>
		</view>
		<view class="page-section" style='align-items: center;justify-content: center;'>
			<view class="vip-button">
				会员专区
			</view>
		</view>
		<view class="page-section">
			<view class="goods-category-block" v-for="(item, index) in goodsList" :key='item.title'>
				<view class="goods-category-title">
					{{item.title}}
				</view>
				<view class="goods-list">
					<view class="goods-list-item" v-for="(goodsItem, goodsIndex) in item.list" :key='goodsItem.id'>
						<view class="goods-list-item-content">
							<image v-bind:src="goodsItem.cover" class="goods-list-item-cover"></image>
							<view class="goods-list-item-info">
								<view class="goods-list-item-row">
									<view class="goods-list-item-name">
										{{goodsItem.name}}
									</view>
								</view>
								<view class="goods-list-item-row">
									<view class="goods-list-item-price">
										￥{{goodsItem.price}}
									</view>
									<image class="shopping-cart-button" src="/static/shoppingcart.png">
									</image>
								</view>
							</view>
						</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import specialBanner from '@/components/specialBanner.vue'
	export default {
		components: {
			specialBanner
		},

		onLoad: function(options) {
			let $this = this;
			setInterval(function() {
				setTimeout(function() {
					let tempIndex = $this.currentNoticeIndex;
					tempIndex++;
					if (tempIndex >= $this.noticeList.length) {
						tempIndex = 0;
					}
					$this.currentNoticeIndex = tempIndex;
					$this.block = 'block' + tempIndex;
				}, 0)
			}, 2000)
		},
		data() {
			return {
				currentCity: '南昌市',
				block: "",
				currentNoticeIndex: 0,
				noticeList: [{
						title: "这是一条通知1,这是一条通知1,这是一条通知1,这是一条通知1,这是一条通知1,这是一条通知1这是一条通知1,这是一条通知1,这是一条通知1这是一条通知1,这是一条通知1,这是一条通知1",
						target: "",
						action: "",
					},
					{
						title: "这是一条通知2,这是一条通知2,这是一条通知2",
						target: "",
						action: "",
					},
					{
						title: "这是一条通知3,这是一条通知3,这是一条通知3",
						target: "",
						action: "",
					},
				],
				optList: [{
						name: '',
						icon: '/static/temp/avatar04.png',
						actionType: '',
						target: '',
					},
					{
						name: '',
						icon: '/static/temp/avatar05.png',
						actionType: '',
						target: '',
					},
					{
						name: '',
						icon: '/static/temp/avatar06.png',
						actionType: '',
						target: '',
					},
					{
						name: '',
						icon: '/static/temp/avatar07.png',
						actionType: '',
						target: '',
					},
				],
				bannerList: [
					{
						picture: 'http://image.mishi.cn/r/yry_h5_test/detail/3_1535359279285.png',
						// title: '七夕将至：时光足够久，韧性也能炖出味',
						// description: '一万年太久，就现在，给你爱',
						path: ''
					},
					{
						picture: 'http://image.mishi.cn/r/yry_h5_test/detail/2_1535359240426.png',
						// title: '新菜上架：无边海洋，找到顺眼的那尾鱼',
						// description: '花中樱，鱼乃鲷花中樱，鱼乃鲷',
						path: ''
					},
					{
						picture: 'http://image.mishi.cn/r/yry_h5_test/detail/1_1535359204228.png',
						// title: '在湘西的烟火气里，发现苗族少女的神明',
						// description: '取材自湘西苗族传统的烟熏文化',
						path: ''
					}, 
					{
						picture: 'http://image.mishi.cn/r/yry_h5_test/detail/4_1535359327213.png',
						// title: '一人宴福利降临，陪伴独自行走的丰盛旅程',
						// description: '在自己的小世界里，日日好日，夜夜好清宵',
						path: ''
					},
				],
				swiperConfig: {
					
					indicatorDots: true,
					indicatorColor: 'rgba(255, 255, 255, .4)',
					indicatorActiveColor: 'rgba(255, 255, 255, 1)',
					autoplay: false,
					interval: 3000,
					duration: 300,
					circular: true,
					previousMargin: '58rpx',
					nextMargin: '58rpx'
				},
				goodsList:[
					{
						title: '轻奢专区',
						list: [
							{
								id: '123',
								name: '商品名称1,商品名称1,商品名称1,商品名称1,商品名称1',
								cover: "https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=1482994069,2351083020&fm=26&gp=0.jpg",
								price: 119
							},
							{
								id: '124',
								name: '商品名称2,商品名称2,商品名称2,商品名称2,商品名称2',
								cover: "https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=2773704381,3675424550&fm=26&gp=0.jpg",
								price: 116
							},
							{
								id: '125',
								name: '商品名称3,商品名称3,商品名称3,商品名称3,商品名称3',
								cover: "https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1593294764780&di=04fd2c8a259ef1ccf131accd2e68855e&imgtype=0&src=http%3A%2F%2Fimg11.360buyimg.com%2FpopWaterMark%2Fjfs%2Ft1609%2F296%2F110429150%2F328595%2F74e85267%2F55599f86N3f21816a.jpg",
								price: 117
							},
							{
								id: '126',
								name: '商品名称4,商品名称4,商品名称4,商品名称4,商品名称4',
								cover: "https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=2495552315,3008814534&fm=26&gp=0.jpg",
								price: 118
							},
						]
					}
				]
			}
		},
		methods: {
			tapButtonItem: function(index) {
				console.log('tapBannerItemAtIndex:', index);
			}
		}
	}
</script>

<style>
	page{
		background: rgb(250,250,250);
	}
	.page-section {
		display: flex;
		flex-direction: column;
	}

	.page-row {
		display: flex;
		flex-direction: row;
	}

	.city-select-box {
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: center;
		padding: 10upx 20upx;
		background: #ee2c2c;
		margin: 5upx 10upx;
		border-radius: 10upx;
		height: 50upx;
		line-height: 50upx;
	}

	.city-select-button {
		font-size: 32upx;
		color: #FFFFFF;
		background-color: #00000000;
	}

	.city-select-image {
		width: 32upx;
		height: 32upx;
	}

	.search-box {
		height: 50upx;
		padding: 10upx 25upx;
		display: flex;
		flex-direction: row;
		align-items: center;
		border: 1upx solid #bfbfbf;
		border-radius: 35upx;
		flex-grow: 1;
		margin: 5upx 10upx;
	}

	.search-image {
		width: 32upx;
		height: 32upx;
		margin: 5px;
	}

	.search-input {
		font-size: 32upx;
		color: #BFBFBF;
	}

	.section-content {
		width: 95%;
		margin: 15upx;
		border-radius: 15upx;
		background: #ffee78;
		padding: 15upx;
	}

	.opt-area {
		display: flex;
		flex-direction: row;
		align-items: center;
		flex-wrap: wrap;
		padding: 10upx 15upx;
	}

	.opt-button {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		width: 25%;
	}

	.opt-icon {
		width: 100upx;
		height: 100upx;
	}

	.notic-area {
		display: flex;
		flex-direction: row;
		align-items: center;
	}

	.notice-icon {
		width: 50upx;
		height: 50upx;
	}

	.notice-list {
		width: 90%;
		max-height: 60upx;
	}

	.notice-item {
		margin: 10upx;
		height: 50upx;
		font-size: 26upx;
		line-height: 50upx;
		white-space: nowrap;
		text-overflow: ellipsis;
		overflow: hidden;
	}

	.vip-button {
		width: 80%;
		height: 180upx;
		border-radius: 90upx;
		line-height: 180upx;
		text-align: center;
		font-size: 45upx;
		font-weight: bold;
		letter-spacing: 10upx;
		background-color: #DD524D;
		color: #FFFFFF;
	}
	.goods-category-block{
		display: flex;
		flex-direction: column;
	}
	.goods-category-title{
		font-size: 40upx;
		color: #778899;
		font-weight: bold;
		padding: 10upx 25upx;
	}
	.goods-list{
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
		align-items: center;
	}
	.goods-list-item{
		width: 50%;
		display: flex;
		align-items: center;
		justify-content: center;
	}
	.goods-list-item-content{
		width: 90%;
		margin: 15upx auto;
		display: flex;
		flex-direction: column;
		border-radius: 15upx;
		background-color: #FFFFFF;
		overflow: hidden;
	}
	.goods-list-item-cover{
		width: 100%;
		height: 300upx;
	}
	.goods-list-item-info{
		display: flex;
		flex-direction: column;
	}
	.goods-list-item-row{
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: space-between;
		padding: 8upx 20upx;
	}
	.goods-list-item-name{
		font-size: 32upx;
		color: #AAAAAA;
		overflow: hidden;
		text-overflow: ellipsis;
		display: -webkit-box;
		-webkit-line-clamp: 2;
		-webkit-box-orient: vertical;
	}
	.goods-list-item-price{
		font-size: 33upx;
		color: #ee2c2c;
		font-weight: bold;
	}
	.shopping-cart-button{
		width: 50upx;
		height: 50upx;
	}
</style>
