<template>
	<view class="index">
		<view class="index-top">
			<image src="../../static/image/banner.png" mode=""></image>
		</view>
		<view class="index-center">
			<view class="index-center-top">
				<image src="../../static/image/logo.png" mode=""></image>
			</view>
			<view class="index-center-bottom">趣砍App</view>
		</view>
		<view class="index-bottom">
			<view class="index-bottom-top" @click="handleIosDown">
				<image src="../../static/image/pingguo.png" mode=""></image>
				<view class="index-bottom-top-name">立即下载ios版</view>
			</view>
			<view class="index-bottom-footer" @click="handleAndDown">
				<image src="../../static/image/anzhuo-2.png" mode=""></image>
				<view class="index-bottom-footer-name">立即下载安卓版</view>
			</view>
		</view>
		<tip-open-browser :openBrowserFlag="openBrowserFlag"></tip-open-browser>
	</view>
</template>

<script>
	import tipOpenBrowser from './open-browser'
	export default {
		data() {
			return {
				openBrowserFlag: false,
				androidDown: 'http://qukan-h5.bajiaostar.com/qukan.apk',
				iosDown: 'https://apps.apple.com/cn/app/gg%E6%9D%A5%E9%80%81/id1494559484',
			}
		},
		components: {
		    tipOpenBrowser
		},
		onLoad() {
			this.getDownPath()
		},
		methods: {
			getDownPath() {
				if(/android/i.test(navigator.userAgent)){
				   //Android平台下浏览器
				    if (this.isWeiXin()) this.openBrowserFlag = true 
					else {
						 this.openBrowserFlag = false
						 // window.location.href = this.androidDown
					}
				   
				}
			},
			// 判断是否微信浏览器
			isWeiXin() {
				var ua = window.navigator.userAgent.toLowerCase()
				if (ua.match(/MicroMessenger/i) == 'micromessenger') {
					return true
				} else {
					return false
				}
			},
			// ios下载
			handleIosDown () {
				uni.showToast({
					icon: 'none',
					title: '暂未开通'
				})
			},
			handleAndDown () {
				window.location.href = this.androidDown
			}
		}
	}
</script>

<style lang="less">
	.index{
		.index-top{
			width: 100%;
			height: 476rpx;
			position: relative;
			image{
				width: 100%;
				height: 100%;
			}
		}
		.index-center{
			width: 100%;
			text-align: center;
			position: absolute;
			top: 25.3%;
			.index-center-top{
				
				image{
					width: 200rpx;
					height: 200rpx;
					box-sizing: border-box;
					box-shadow: 0 2px 10px 0 rgba(0,0,0,0.10);
				}
			}
			.index-center-bottom{
				padding-top: 50rpx;
				box-sizing: border-box;
				font-family: PingFangSC-Medium;
				font-size: 22px;
				color: #000000;
				font-weight: bold;
			}
		}
		.index-bottom{
			width: 100%;
			text-align: center;
			margin: 0 auto;
			position: absolute;
			bottom: 262rpx;
			// left: 50%;
			// transform: translateX(-50%);
			display: flex;
			flex-direction: column;
			justify-content: center;
			align-items: center;
			image{
				width: 42rpx;
				height: 42rpx;
				margin-right: 20rpx;
				box-sizing: border-box;
			}
			.index-bottom-top, .index-bottom-footer{
				width: 540rpx;
				height: 100rpx;
				display: flex;
				text-align: center;
				justify-content: center;
				align-items: center;
				background-image: linear-gradient(180deg, #FF7360 0%, #C9281C 100%);
				border-radius: 25px;
				font-family: PingFangSC-Regular;
				font-size: 17px;
				color: #FFFFFF;
				letter-spacing: -0.41px;
				text-align: justify;
			}
			.index-bottom-footer{
				margin-top: 50rpx;
				box-sizing: border-box;
				image{
					transform: translateX(8rpx);
				}
				.index-bottom-footer-name{
					transform: translateX(8rpx);
				}
			}
		}
	}
</style>
