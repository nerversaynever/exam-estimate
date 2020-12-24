<template>
	<view class="page-view">
		<view class="group">
			<view class="row">
				<view class="name">您的报考区域</view>
				<view class="select">
					 <picker mode="selector" :value="formInfo.area" @change="selectArea" :range="areaList">
							<view class="uni-input">{{areaList[formInfo.area]}}</view>
					</picker>
					<image src="/static/down.png" mode="widthFix" class="down"></image>
				</view>
			</view>
			<view class="row">
				<view class="name">您的报考院校</view>
				<view class="select">
					 <picker mode="selector" :value="formInfo.school" @change="selectSchool" :range="schoolList">
							<view class="uni-input">{{schoolList[formInfo.school]}}</view>
					</picker>
					<image src="/static/down.png" mode="widthFix" class="down"></image>
				</view>
			</view>
			<view class="row">
				<view class="name">您的报考专业</view>
				<view class="select">
					 <picker mode="selector" :value="formInfo.major" @change="selectMajor" :range="majorList">
							<view class="uni-input">{{majorList[formInfo.major]}}</view>
					</picker>
					<image src="/static/down.png" mode="widthFix" class="down"></image>
				</view>
			</view>
			<view class="row">
				<view class="name">您参考院校正常/提前批次</view>
				<view class="select">
					 <picker mode="selector" :value="formInfo.batch" @change="selectBatch" :range="batchList">
							<view class="uni-input">{{batchList[formInfo.batch]}}</view>
					</picker>
					<image src="/static/down.png" mode="widthFix" class="down"></image>
				</view>
			</view>
			<view class="submitBtn margin-top-lg" @tap="submit">根据估分查上岸概率</view>
		</view>
		<view class="estimate-result" v-if="isViewResult">
			<view class="title text-center">北京大学光华学院{{formInfo.result=='pass'?"2021复试线":"往年分数线"}}</view>
			<view class="tablebox">
				<view class="table">
					<view class="table-hd flex">
						<span class="flex-sub" v-if="formInfo.result=='pass'">报考专业</span>
						<span>复试线</span>
						<span class="flex-sub">管综分数线</span>
						<span class="flex-sub">英语单科分数线</span>
						
					</view>
					<view class="table-bd">
						<view class="table-td flex">
							<span class="flex-sub" v-if="formInfo.result=='pass'">EMBA</span>
							<span>175</span>
							<span class="flex-sub">88</span>
							<span class="flex-sub">42</span>
						</view>
						
					</view>
					
				</view>
			</view>
			<view class="result-con text-center">
				<template v-if="formInfo.result=='pass'">
					<image src="/static/smile.png" class="icon" mode="widthFix"></image>
					 <view>根据往年复试线，恭喜你，过线了</view>
				</template>
				<template v-if="formInfo.result!='pass'">
					<image src="/static/cry.png" class="icon" mode="widthFix"></image>
					<view>根据往年复试线，很遗憾，未过目标院校线</view>
					<view class="warn">
						<text class="defultColor">果芽MBA</text>温馨提示：
						<view class="tip">估分涉及主观题以及每年国家线/复试线会有波动，请持续关注后续分数线公布、国家线发布以及接受调剂院校汇总情况</view>
					</view>
					<!-- <view>根据往年复试线，很遗憾，未过线</view>
					<view class="tip">温馨提示：但估分及复试线每年都有波动，请关注后续分数公布及国家线发布情况</view> -->
				</template>
				<view class="scan flex">
					<image src="/static/code.png" class="code"></image>
					<view class="des flex-sub">
						<view class="tip defultColor">扫码二维码</view>
						<template v-if="formInfo.result=='pass'">
							<view class="defultColor">1.回复【复试难度评估】</view>
							<view>择校老师根据<text class="orange">往年目标院校分数段</text>人工回复上岸难度</view>					
							<view class="defultColor">2.回复【复试课程】</view>				
							<view>领取果芽复试福利课程</view>					
							<view class="defultColor">3.回复【复试资料】</view>
							<view>领取果芽复试资料包</view>
						</template>
						<template v-if="formInfo.result!='pass'">
							<view class="defultColor">1.回复【调剂院校汇总】</view>
							<view>领取往年调剂院校汇总资料</view>					
							<view class="defultColor">2.回复【二战】</view>				
							<view>领取果芽22级笔试面试助力包</view>					
							<view class="defultColor">3.回复【进群】</view>
							<view>加入果芽22级备考群</view>
							<view class="defultColor">4.回复【择校评估】</view>
							<view>人工大数据重新匹配目标院校</view>
						</template>
					</view>
				</view>
				<view class="defaultBtn margin-top-lg" @tap="share">分享给其他好友</view>
			</view>
			
		</view>
		
	</view>
</template>

<script>
	export default {
		name:"probability",
		data() {
			return {
				formInfo:{
					area:"",
					school:"",
					major:"",
					batch:"",
					result:"pass"
				},
				areaList:[],
				schoolList:[],
				majorList:["MBA","MPAcc","MEM","MPA","MLIS","MTA","MAud","EMBA"],
				/* majorList:["工商管理硕士(MBA)","会计硕士(MPAcc)","工程管理硕士(MEM)","公共管理硕士(MPA)","图书情报硕士(MLIS)","旅游管理硕士(MTA)","审计硕士(MAud)","高级管理人员工商管理硕士(EMBA)"], */
				batchList:[],
				isViewResult:false,
			};
		},
		methods:{
			selectArea(e){
				this.formInfo.area = e.target.value
			},
			//选择院校
			selectSchool(e){
				this.formInfo.school = e.target.value
			},
			//选择专业
			selectMajor(e){
				this.formInfo.major = e.target.value
			},
			//选择批次
			selectBatch(e){
				this.formInfo.batch = e.target.value
			},
			//提交
			submit(){
				this.isViewResult=true;
			},
			//分享
			share(){
				uni.share({
				    provider: "weixin",
				    scene: "WXSceneSession",
				    type: 1,
				    summary: "我正在使用HBuilderX开发uni-app，赶紧跟我一起来体验！",
				    success: function (res) {
				        console.log("success:" + JSON.stringify(res));
				    },
				    fail: function (err) {
				        console.log("fail:" + JSON.stringify(err));
				    }
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
	.group {
		margin: 0 40rpx;
		padding-top: 20rpx;
		.row {
			font-size: 32upx;

			.name {
				line-height: 66rpx;
				margin-right: 20upx;
				font-weight: 500;
				
			}
		}

		.row+.row {
			margin-top: 20upx;
		}

		input,picker {
			color: #999999;
			height: 66rpx;
			background: #FFFFFF;
			border-radius: 10upx;
			border: 2rpx solid #aaaaaa;
			padding-left: 20upx;
		}

		.select {
			position: relative;
			input,.uni-input {
				color: #333333;
			}
			.uni-input{
				height: 66rpx;
				line-height: 66rpx;
			}
			.down {
				width: 32upx;
				height: 32upx;
				position: absolute;
				top: 50%;
				transform: translate(-50%, -50%);
				-webkit-transform: translate(-50%, -50%);
				-ms-transform: translate(-50%, -50%);
				right: 20upx;
			}
		}

		.margin-top-lg {
			margin-top: 60rpx;
		}
	}
	.estimate-result{
		margin: 20rpx 40rpx 0;
		.title{
			font-size: 32upx;
			font-weight: 500;
		}
		.result-con {
			margin: 20rpx 0 60rpx;
			
			.tip{
				text-align: left;
			}
			.icon{
				width: 100rpx;
				display: block;
				margin: 0 auto;
				margin-bottom: 10rpx;
			}
			.warn{
				margin-top: 20rpx;
				background: #F2F2F2;
				padding: 10rpx 20rpx;
				line-height: 40rpx;
			}
		}
	}
	.tablebox {
		padding: 30upx 0;
		color: #434040;
		font-size: 26upx;
	
		.table {
			border: 1px solid #dbdbdb;
			text-align: center;
	
			.table-hd,
			.table-bd .table-td,
			.table-ft {
				align-items: stretch;
	
				span {
					width: 93upx;
					padding: 25upx 0;
	
					&:first-child {
						width: 130upx;
					}
	
					&+span {
						border-left: 1px solid #dbdbdb;
					}
				}
			}
	
			.table-hd {
				border-bottom: 1px solid #dbdbdb;
				height: 75upx;
				background: #db6553;
				color: #ffffff;
				font-size: 28upx;
				font-weight: bold;
			}
	
			.table-bd .table-td {
				color: #6c6c6c;
				font-size: 25upx;
	
				&+.table-td {
					border-top: 1px solid #dbdbdb;
				}
	
				&:nth-child(even) {
					background: #f9f9f9;
				}
			}
	
			.table-bd {
				border-bottom: 1px solid #dbdbdb;
			}
	
			.table-ft {
				color: #fd3c3e;
				font-size: 26upx;
	
				height: 74upx;
	
				.text-right {
					color: #2e2e2e;
					font-size: 28upx;
					font-weight: bold;
					padding-right: 54upx;
					color: #2e2e2e;
				}
			}
		}
	}
	.scan{
		margin:40rpx 0;
		text-align: left;
		position: relative;
		.code{
			width: 260rpx;
			height: 260rpx;
			display: block;
			position: absolute;
			top: 50%;
			transform: translateY(-50%);
		}
		.des{
			margin-left: 280rpx;
			font-size: 28rpx;
			line-height: 40rpx;
			.tip{
				margin-bottom: 10rpx;
			}
		}
	}
</style>
