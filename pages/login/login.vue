<template>
	<view class="d-flex align-c f-c">
	  <view class="d-flex j-center p-fixed" style="top:20%;">
<image style="width: 300rpx;" src="/static/home.png" mode="widthFix" />
	  </view>
	  <view class="p-fixed font-3" style="bottom:20%;width:680rpx;text-align: center;">
		  
<!-- <button class="bcolor c" style="height:100rpx;line-height:100rpx;"
 open-type="getPhoneNumber" @getphonenumber="getPhoneNumber">微信一键登录</button> -->
 
	<view class="bcolor c" style="height:100rpx;line-height:100rpx;">
		微信一键登录
	</view>
	 <view class="border-7 mt-4 c-9" style="height:100rpx;line-height:100rpx;">
			手机/账号登录
		</view>
	  	</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				
			}
		},
		methods:{
	// getPhoneNumber: function(e) {
	// 				console.log(e,'llllllll');
	// 				if (e.detail.errMsg == 'getPhoneNumber:fail user deny') {
	 
	// 				} else {
	 
	// 				}
	// 				// console.log(JSON.stringify(e.encryptedData));
	// 				// 				console.log(JSON.stringify(e.iv));
	// 			}
		}
	}
</script>

<style>

</style>
