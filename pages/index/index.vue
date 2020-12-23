<template>
	<view class="page-view">
		<view class="index">
			<image class="logo" src="/static/logo.png"></image>
			<view class="content" >
				<text class="title">2021管理类联考</text>
				<text class="name">在线估分</text>
				<text class="des">查排名 估上岸概率</text>
				<view class="label shadow-warp">
					适合专业
					MBA/MEM/MPA/EMBA
				</view>
			</view>
		</view>
		<view class="content-bottom">
			<text>全国已有<text class="num">231</text>位考生完成估分</text>
			<button class="defaultBtn" @click="estimate">立即估算</button>
		</view>
	</view>
</template>

<script>
	export default {
		name:"index",
		data() {
			return {
				
			}
		},
		onLoad() {

		},
		methods: {
			//立即估算
			estimate(){
				uni.navigateTo({
					url: "/pages/answer/answer"
				});
			}
		}
	}
</script>

<style lang="scss">
	page,
	.page-view{
		height: 100%;
		position: relative;
		background: #fff;	
	}
	.index {
		background: #db6553;
		.logo {
			position: fixed;
			height: 80rpx;
			width: 80rpx;
			border-radius: 100%;
		}
	}
	.content{
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		color: #fff;
		padding-bottom: 250rpx;
		position: relative;
		.title{
			
			font-size: 70rpx;
			color: #fff;
		}
		.name{
			margin-top: 30rpx;
			font-size: 70rpx;
			color: #fff;
		}
		.des{
			margin-top: 30rpx;
			font-size: 40rpx;
		}
		.label{
			position: absolute;
			left: 20rpx;
			right: 20rpx;
			margin: 0 auto;
			bottom: -60rpx;
			font-size: 40rpx;
			background: #fff;
			color: #8799a3;
			padding: 40rpx 60rpx;
			border-radius: 100rpx;
			text-align: center;
		}
	}
	
	
	.content-bottom{
		margin-top: 150rpx;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		color: #333333;
		font-size: 40rpx;
		.num{
			color: #db6553;
		}
		.defaultBtn{
			margin-top: 30rpx;
			width: 500rpx;
		}
	}
	
</style>
