<template>
	<view class="page-view">
		<view class="tabs flex">
			<view v-for="(item,index) in tabs" :key="index" @tap="tabsChange(index)" :class="{'active':tabsCur==index}" class="tabs-item flex-sub padding text-center">
				{{item}}
			</view>
		</view>
		<view class="tabbar flex" id="tabInList">
			<view v-for="(item,index) in tabList" :key="index" @tap="tabChange(index)" :class="{'defultColor':tabCur==index}" class="tab-item flex-sub text-center">
				{{item}}
			</view>
		</view>
		<mescroll-body ref="mescrollRef" @init="mescrollInit"  @scroll="scroll"
		 :top="topH" :down="downOption" @down="downCallback" :up="upOption" @up="upCallback">
		<view class="questions">
			<view class="des defultColor">{{tabList[tabCur]}}</view>
			<view class="questions-con">
				<question-item v-for="(item,index) in questionList" :info="item" :type="tabCur" :index="index" :list="questionList"></question-item>
				<!-- <view class="questions-item" v-for="(item,index) in questionList">
					<view class="number cu-tag">第{{item.number}}题</view>
					<view class="text">{{item.text}}</view>
					<view class="operate  flex align-center" v-if="tabCur!=3">
						<button class="flex-sub btn" :class="{'success':operateType=='success'}" @tap="responde('success')">√ 答对了</button>
						<button class="flex-sub btn" :class="{'error':operateType=='error'}" @tap="responde('error')">× 答错了</button>
					</view>
					<view class="mark flex" v-if="tabCur==3">
						<text>自我评分</text><input type="number" class="input-number flex-sub" />
					</view>
				</view> -->
			</view>
		</view>
		
		</mescroll-body>
		<view class="bottom-operate">
			<view class="defaultBtn" @tap="viewScore">估分数    查排名    评概率</view>
		</view>
	</view>
</template>

<script>
	import questionItem from '@/components/questionItem.vue';
	import MescrollMixin from '@/components/mescroll-uni/mescroll-mixins.js';
	export default {
		name:'answer',
		mixins: [MescrollMixin],
		components: {
			questionItem
		},
		data() {
			return {
				tabs:["综合能力 0分","英语 (二)"],
				tabsCur:0,
				tabList:["问题求解","条件充分性判断","逻辑推理","写作"],
				tabCur:0,
				isShowSticky: false,
				topH: 196,
				navTop: 0,
				upOption: {
					// auto: false // 不自动加载
					noMoreSize: 2,
					page: {
						size: 20
					}
				},
				isInit: false,
				questionList:[{
					number:1,
					text:"测试",
					operateType:''
				},{
					number:2,
					text:"测试",
					operateType:''
				},
				{
					number:3,
					text:"测试",
					operateType:''
				},
				{
					number:4,
					text:"测试",
					operateType:''
				},
				{
					number:5,
					text:"测试",
					operateType:''
				}],
				operateType:'',//操作类型
				
			};
		},
		methods: {
			// 下拉刷新的回调
			downCallback() {
				// mixin默认resetUpScroll
				
			},
			upCallback(mescroll) {
				if (!this.navTop) this.setNavTop();
				
			},
			tabsChange(index) {
				this.tabsCur=index;
			},
			setNavTop() {
				let view = uni.createSelectorQuery().select('#tabInList');
				view.boundingClientRect(data => {
					this.navTop = (data && data.top) || 200; // 到屏幕顶部的距离
				}).exec();
			},
			tabChange(index){
				this.tabCur=index;
			},
			//查看分数和排名
			viewScore(){
				uni.navigateTo({
					url: "/pages/scoreAndRank/scoreAndRank"
				});
			},
			//作答
			responde(val){
				this.operateType=val;
			}
		},
		onPageScroll(e) {
			console.log('滚动条位置 = ' + e.scrollTop + ', navTop = ' + e.scrollTop);
			e.scrollTop = e.scrollTop;
			if (e.scrollTop >= this.navTop) {
				this.isShowSticky = true; // 显示悬浮菜单
			} else {
				this.isShowSticky = false; // 隐藏悬浮菜单
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
	.tabs{
		z-index: 9999;
		position: fixed;
		top: 0;
		left: 0;
		width:100%;
		border-bottom: 2rpx solid #2C405A;
		.tabs-item{
			background-color: #fff;
			color: #333333;
			font-size: 30rpx;
		}
		.tabs-item.active{
			background-color: #db6553;
			color: #fff;
		}
	}
	.tabbar{
		z-index: 9999;
		position: fixed;
		top: 98rpx;
		left: 0;
		width:100%;
		background-color: #fff;
		width: 100%;
		border-bottom: 2rpx solid #2C405A;
		.tab-item{
			color: #333333;
			padding: 30rpx 0;
		}
	}
	.questions{
		padding:0 40rpx 40rpx;
		.questions-item{
					margin-top: 20rpx;
					padding-bottom: 20rpx;
					.number{
						background: #db6553;
						color: #fff;
						border-radius: 8rpx;
					}
					.text{
						margin:10rpx 0 30rpx;
					}
					.operate{
						.btn{
							color: #2C405A;
							text-align: center;
							border-radius: 8upx;
							background: #fff;
							height: 50upx;
							line-height: 50upx;
							font-size: 28upx;
							border: 2rpx solid #2C405A;
							display: block;
						}
						.btn + .btn {
							margin-left: 118upx;
						}
						.btn.success{
							background: #39b54a;
							color: #fff;
							border: 2rpx solid #39b54a;
						}
						.btn.error{
							background: #db6553;
							color: #fff;
							border: 2rpx solid #db6553;
						}
						
					}
					
					.mark{
						width: 100%;
						padding: 10rpx;
						background: #DDDDDD;
						border-radius: 8rpx;
						text{
							line-height: 1.4rem;
						}
						.input-number{
							background-color: #fff;
							border-radius: 8rpx;
							padding:0 10rpx;
							margin-left: 10rpx;
						}
					}
				}
				.questions-item:not(:last-child){
					border-bottom: 2rpx solid #aaaaaa;
				}
		
	}
	.bottom-operate{
		position: fixed;
		bottom: 0;
		width: 100%;
		z-index: 9999;
		.defaultBtn{
			border-radius: 0;
		}
	}

</style>
