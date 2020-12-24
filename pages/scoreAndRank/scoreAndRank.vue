<template>
	<view class="page-view">
		<view class="title text-center">
			<view>
				感谢使用<text class="name">果芽MBA</text>估分系统
			</view>
			<view class="des">您的估分成绩</view>
		</view>
		<view class="result flex">
			<view class="result-item flex-sub ">
				<view class="result-item-title flex justify-between">
					<text class="item">综合能力</text>
					<text class="score">48分</text>
				</view>
				<view class="item-result flex justify-between">
					<text class="item">问题求解</text>
					<text class="score">12</text>
				</view>
				<view class="item-result flex justify-between">
					<text class="item">条件充分性判断</text>
					<text class="score">3</text>
				</view>
				<view class="item-result flex justify-between">
					<text class="item">逻辑推理</text>
					<text class="score">4</text>
				</view>
				<view class="item-result flex justify-between">
					<text class="item">写作</text>
					<text class="score">0</text>
				</view>
			</view>
			<view class="result-item flex-sub">
				<view class="result-item-title  flex justify-between">
					<text class="item">英语（二）</text>
					<text class="score">48分</text>
				</view>
				<view class="item-result flex justify-between">
					<text class="item">完形填空</text>
					<text class="score">12</text>
				</view>
				<view class="item-result flex justify-between">
					<text class="item">阅读理解</text>
					<text class="score">3</text>
				</view>
				<view class="item-result flex justify-between">
					<text class="item">翻译</text>
					<text class="score">4</text>
				</view>
				<view class="item-result flex justify-between">
					<text class="item">写作</text>
					<text class="score">0</text>
				</view>
			</view>
		</view>
		<view class="rank flex">
			<view class="rank-item  flex-sub">
				<view class="number">178</view>
				<view>总分</view>
			</view>
			<view class="rank-item flex-sub">
				<view class="number">21</view>
				<view>排名</view>
			</view>
			<view class="rank-item flex-sub">
				<view class="number">231</view>
				<view>估分人数</view>
			</view>
		</view>
		<view class="operate">
			<button class="defaultBtn" @click="estimate">再次估分</button>
			<button class="defaultBtn" @click="viewProbability">查看上岸概率</button>
		</view>
		<view class="scan flex">
			<image src="/static/code.png" class="code" mode="widthFix"></image>
			<view class="des flex-sub">
				<view class="tip defultColor">扫码免费领取</view>
				<view>【2021联考复试全套资料】</view>		
				<view>1.英语听力真题及录音文件</view>					
				<view>2.常考的复试政治资料</view>				
				<view>3.高频英语口语问题及应答模板</view>					
				<view>4.复试往年高频真题资料</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name:"scoreAndRank",
		data() {
			return {
				
			};
		},
		methods:{
			//再次估分
			estimate(){
				uni.redirectTo({
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
		background: #fff;	
	}
	.title{
		padding: 40rpx;
		font-size: 40rpx;
		.name{
			color: #db6553;
		}
	}
	.result{
		border: 2rpx solid #aaaaaa;
		border-radius: 8upx;
		margin:20rpx 40rpx;
		.result-item {
			padding: 20rpx 40rpx;
			border-right:2rpx solid #aaaaaa;
			.result-item-title{
				font-size: 30rpx;
				.item{
					font-weight: bold;
				}
				.score{
					color: #db6553;
					margin-left: 20rpx;
					font-weight: bold;
				}
			}
			.item-result{
				padding: 5rpx 0;
				font-size: 28rpx;
				.score{
					margin-left: 20rpx;
					
				}
			}
		}
	}
	.rank{
		margin: 30rpx 40rpx;
		text-align: center;
		.rank-item{
			font-size: 30rpx;
			font-weight: bold;
		}
	}
	.operate{
		margin: 40rpx 0;
		.defaultBtn{
			margin-top: 30rpx;
			width: 400rpx;
			line-height: 80rpx;
		}
	}
	.scan{
		margin:20rpx 40rpx;
		.code{
			width: 280rpx;
			display: block;
		}
		.des{
			margin-left: 20rpx;
			font-size: 28rpx;
			line-height: 40rpx;
			.tip{
				margin-bottom: 10rpx;
			}
		}
	}
</style>
