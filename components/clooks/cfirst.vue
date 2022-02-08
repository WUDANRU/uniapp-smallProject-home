<template>
	<view class="bd-white" style="padding:24rpx;">
	<c-title></c-title>
	<view class="d-flex" style="flex-wrap: wrap;">
		<block  v-for="(i,ix) in num" :key="ix">
		<image class="mt-1 ml-1" style="width:200rpx;" mode="widthFix" src="/static/picture.png"></image>
		</block>
		<view v-if="cfirst"  class="mt-2 d-flex align-c" style="width:100%;height:80rpx;background-color: #f2f5f5;">
			<slot ></slot>
		</view>
	</view>
	</view>
</template>

<script>
	import cTitle from '@/components/crepeat/ctitle.vue'
	export default {
		components:{
			cTitle
		},
		props:{
			cfirst:false,
			num:Number,
		}
		}
</script>

<style>
</style>
