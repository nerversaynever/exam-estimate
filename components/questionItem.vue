<template>
	<view class="questions-item" >
		<view class="number cu-tag">第{{info.number}}题</view>
		<view class="text">{{info.text}}</view>
		{{JSON.stringify(info)}}
		<view class="operate  flex align-center" v-if="type!=3">			
			<button class="flex-sub btn" :class="{'success':info.operateType=='success'}" @tap="responde('success')">√ 答对了</button>
			<button class="flex-sub btn" :class="{'error':info.operateType=='error'}" @tap="responde('error')">× 答错了</button>
		</view>
		<view class="mark flex" v-if="type==3">
			<text>自我评分</text><input type="number" class="input-number flex-sub" />
		</view>
	</view>
</template>

<script>
	export default {
		name:"questionItem",
		props: {
			type:{
				type: Number,
			},
			info: {
				type: Object,
				default: {}
			},
			list:{
				type: Array,
				default:[]
			},
			index:{
				type: Number,
				default:0,
			}
		},
		data() {
			return {
				
			};
		},
		methods:{
			responde(val){
				//this.list[this.index].operateType=val;
				this.info.operateType=val;
				this.$set(this.list,this.index,this.info)
				console.log(JSON.stringify(this.info))
			}
		}
		
	}
</script>

<style lang="scss" scoped>

</style>
