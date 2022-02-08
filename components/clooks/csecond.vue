<template>
	<view class="mt-3 bd-white" style="padding:24rpx;">
	<c-title></c-title>
<view class="mb-2">
	品牌宣传
</view>
<image @click="showVideo" style="margin:0 auto;" src="/static/photo.png" mode="widthFix"></image>
<view v-if="csecond" class="mt-2 d-flex align-c" style="width:100%;height:80rpx;background-color: #f2f5f5;">
  <slot></slot>
  <!-- <slot name="vi"></slot> -->
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
			csecond:false,
		},
		methods:{
			showVideo(){
			uni.navigateTo({
				url:'/pages/video/video'
			})
			},
		}
		}
</script>

<style>
</style>
