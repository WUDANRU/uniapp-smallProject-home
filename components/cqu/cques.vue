<template>
	<view v-if="qt===item2.text">
			<view class="">
				<image class="mr-1" :src="item2.qucover" style="width:36rpx;" mode="widthFix"></image>
				<text>{{item2.title}}</text>
			</view>
			<view class="mt-1">
				<image class="mr-1" :src="item2.ancover" style="width:36rpx;" mode="widthFix"></image>
				<text class="mr-1">{{item2.main}}</text>
				<text class="border-2 c-2" style="font-size:20rpx;padding:3rpx;">{{item2.sec}}</text>
			</view>
			<view class="mt-1">
				<image class="mr-1" :src="item2.jhcover" style="width:80rpx;" mode="widthFix"></image>
				<text style="overflow: hidden;text-overflow: ellipsis;display: -webkit-box; -webkit-line-clamp: 2; -webkit-box-orient: vertical;">{{item2.fonts}}</text>
			</view>
		  <view class="border my-5" style=""></view>
		</view>
</template>

<script>
	export default {
		props:{
			item2:Object,
			qList:Array,
			qt:String
		},
		onLoad(){
			console.log(qList.qtitle,'qList.qtitle')
		},
		data() {
			return {
				
			}
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
