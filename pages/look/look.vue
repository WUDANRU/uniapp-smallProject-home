<template>
	<view>
		<scroll-view scroll-y style="width:710rpx;margin:0 auto;">
		<view style="padding:0 15rpx;">
			
			<c-first :num="3">
			</c-first>
			
			<template>
			<c-first :num="4" :cfirst="cfirst">
				<slot>
					<image src="/static/people.png" class="ml-2" style="width:60rpx;" mode="widthFix"></image>
					<text class="ml-1 mr-1">林东艺</text>
					<text style="color:#676c73;">发布视频动态</text>
				</slot>
			</c-first>
			</template>
			
			<template>
			<c-second :csecond="csecond">
				<!-- <view slot="vi"> -->
				<slot>
					<image src="/static/people.png" class="ml-2 d-flex" style="width:60rpx;" mode="widthFix"></image>
					<text class="ml-1 mr-1">林东艺</text>
					<text style="color:#676c73;">发布视频动态</text>
				</slot>
				<!-- </view> -->
			</c-second>
			</template>

			<view style="height:130rpx;"></view>
		</view>
		</scroll-view>

			<template>
<!-- transform: translateX(20px); transition: right 过渡时长 linear 延迟;-->
		<view @click="lookCli" :style="cli?'right:-60px;transition: right .2s linear 0s;':'right:30px;transition: right .2s linear 0s;'"
		style="position: fixed;bottom:90px;width: 200rpx;height:80rpx;box-shadow: 0 0 2px 1px #f2f4f3;" 
		class="bd-white d-flex align-c j-center b-radius-3">
			<text class="iconfont" :class="cli?'icon-dingyue c-4':'icon-dingyue1 font-bold'"></text>
			<text class="font-2 pl-1">{{cli?'已订阅':'点击订阅'}}</text>
		</view>
		</template>

	</view>
</template>

<script>
	import cFirst from '@/components/clooks/cfirst.vue'
	import cSecond from '@/components/clooks/csecond.vue'
	export default {
		components:{
			cFirst,
			cSecond
		},
		data() {
			return {
				cfirst:true,
				csecond:true,
				num:3,
				cli:false,
			}
		},
		methods: {
		lookCli(){
			this.cli=!this.cli
		if(this.cli){
			uni.showToast({
				title:'订阅成功',
				icon:'none'
			})
		}else{
			uni.showToast({
				title:'取消订阅',
				icon:'none'
			})
		}
			console.log(this.cli,'this.cli')
		}
		}
	}
</script>

<style>
page{
	background-color: #f2f5f5;
	height:100%;
}
</style>
