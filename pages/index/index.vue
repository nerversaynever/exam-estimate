<template>
	<!-- <view class="page-view"> -->
		<view class="index">
			<image src="/static/banner.png" mode="widthFix" class="banner"></image>
			<!-- <image class="logo" src="/static/logo.png"></image> -->
			
			<view class="index-con-bottom">
				<view><image src="/static/hat.png" mode="widthFix" class="icon"></image>适合专业</view>
				<view class="title">MBA/MEM/MPA/EMBA</view>
				<text>全国已有<text class="num">231</text>位考生完成估分</text>
				<button class="whiteBtn" @click="estimate">立即估分</button>
				<button class="whiteBtn" @tap="showModal" data-target="Modal">直接查上岸概率</button>
			</view>
			<!-- <view class="index-con" >
				
				<text class="title">2021管理类联考</text>
				<text class="name">在线估分</text>
				<text class="des">查排名 估上岸概率</text>
				<view class="label shadow-warp">
					适合专业
					MBA/MEM/MPA/EMBA
				</view>
			</view> -->
			<view class="cu-modal" :class="modalName=='Modal'?'show':''">
				<view class="cu-dialog">
					<view class="cu-bar justify-end">
						<view class="action" @tap="hideModal">
							<text class="cuIcon-close text-red"></text>
						</view>
					</view>
					<view class="modal-con">
						<view class="title">请输入你的估分结果</view>
						<view class="row flex">
							<view class="flex flex-sub">
								<text>总分</text><input class="input-number" type="number"/>
							</view>
							<view class="flex flex-sub">
								<text>管综</text><input class="input-number" type="number"/>
							</view>
							<view class="flex flex-sub">
								<text>英语</text><input class="input-number" type="number" />
							</view>
						</view>
						<view class="operate">
							<button class="defaultBtn" @click="viewProbability">点击查看上岸概率</button>
							<button class="defaultBtn" @click="estimate">不知道分数,需要估分</button>
						</view>
					</view>
				</view>
			</view>
		</view>
		
		
	<!-- </view> -->
</template>

<script>
	export default {
		name:"index",
		data() {
			return {
				modalName:'',
			}
		},
		onLoad() {

		},
		methods: {
			//常看上岸概率
			showModal(e) {
				this.modalName = e.currentTarget.dataset.target
			},
			hideModal(e) {
				this.modalName = null
			},
			//立即估算
			estimate(){
				uni.navigateTo({
					url: "/pages/answer/answer"
				});
			},
			//查看上岸概率
			viewProbability(){
				uni.navigateTo({
					url: "/pages/probability/probability"
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
		background: #db6553;	
	}
	.index {
		position: relative;
		height: 100%;
		line-height: 1.8;
		padding-top: 100upx;
		box-sizing: border-box;
		background: #db6553;
		.logo {
			position: fixed;
			height: 80rpx;
			width: 80rpx;
			border-radius: 100%;
		}
	}
	.banner{
		position: absolute;
		top: 90;
		right: 0;
		width: 100%;
	}
	.index-con-bottom{
		position: absolute;
		top: 780rpx;
		left: 0;
		right: 0;
		margin: 0 auto;
		text-align: center;
		color: #ffffff;
		font-size: 40rpx;
		font-weight: 600;
		.icon{
			width: 100rpx;
			vertical-align: middle;
			margin-top: -6rpx;
			margin-right: 20rpx;			
		}
		.title{
			font-weight: 600;
			font-size: 40rpx;
			background-image:-webkit-linear-gradient(bottom,#EFBAB2,#FEFCFC);			
			-webkit-background-clip:text;
			-webkit-text-fill-color:transparent;
		}
		text{
			font-weight: 600;
		}
		.num{
			color: #E0DC5E;
			font-weight: bold;
			font-size: 40rpx;
		}
		.whiteBtn{
			margin-top: 30rpx;
			width: 500rpx;
			color: #db6553;
			text-align: center;
			border-radius: 45upx;
			background: #FBEFED;
			line-height: 100upx;
			font-weight: 600;
			font-size: 40upx;
			display: block;
		}
	}
	.cu-modal{
		.modal-con{
			padding: 10rpx 40rpx 40rpx;
			text-align: left;
			.title{
				font-size: 30rpx;
			}
			.row{
				margin: 20rpx 0;
				text{
					vertical-align: middle;
					line-height: 1.4rem;
					padding-right: 10rpx;
				}
			}
			
			.input-number{
				border: 2rpx solid #aaaaaa;
				width: 110rpx;
				border-radius: 8rpx;
				padding:0 10rpx;
			}
			.operate{
				margin: 40rpx 0;
				.defaultBtn{
					margin-top: 30rpx;
					width: 400rpx;
					line-height: 80rpx;
				}
			}
			
		}
	}
	
</style>
