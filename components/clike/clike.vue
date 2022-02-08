<template>
	<view>
		<view class="font-4a font-w">
			猜你喜欢
		</view>
		<view class="mt-2" v-for="(iview,iv) in likeAll" :key="iv">
			<view class="d-flex f-r">
			
			<image :src="iview.cover" style="width:280rpx;" mode="widthFix"></image>
			<view class="d-flex f-c ml-2 mr-1" style="flex:1;">
				<view class=""><text class="mr-1a font-3 c-5 bd-2 p-sm">{{iview.one1}}</text>{{iview.one2}}</view>
	            <view class="c-6 font-2a mt-2">{{iview.two}}</view>
				<view class="c-5 mt-1a"><text class="font-bold">{{iview.three}}</text>元/㎡</view>
				<view class=""><text class="c mr-2 bd-3 font-2 px-1">{{iview.four}}</text>
				<text class="c-7 bd-4 px-1 font-2">{{iview.five}}</text>
				<text class="c-7 bd-4 px-1 font-2">{{iview.six}}</text>
				<text class="c-7 bd-4 px-1 font-2">{{iview.seven}}</text>
				</view>
				<view class="mt-2">
					<view class="d-flex f-r j-sb align-c">
						<view class="">
							<text class="bd-5 c font-2 px-1">荐</text>
							<text class="font-2 c-8 ml-1">{{iview.text1}}</text>
						</view>
						<text style="font-size:20rpx;" @click="iconView(iview)" class="c-8" :class="iview.flag?'iconfont icon-jiantouxia':'iconfont icon-jiantoushang'"></text>
					</view>
					<view class="d-none f-r j-sb align-c mt-1a" :style="iview.flag?'display:none;':'display:flex;'">
						<view class="">
							<text class="bd-5 c font-2 px-1 bd-6">看</text>
							<text class="font-2 c-8 ml-1">{{iview.text2}}</text>
						</view>
					</view>
				</view>
			</view>
			</view>
			
			<view class="d-flex f-c border-4 my-3a"></view>
		</view>
	</view>
</template>

<script>
	export default {
		data(){
			return{
				// flag:false,
				likeAll:[
					{
						cover:"/static/ph.png",
						one1:"新盘",
						one2:"中骏丽景府二期",
						two:"晋江市 磁灶 | 建面97-143㎡",
						three:"7700",
						four:"在售",
						five:"住宅",
						six:"配套纯熟",
						seven:"公园",
						text1:"学府旁超万平绿化中骏大盘",
						text2:"预约看房，免费专车往返接送",
						flag:"false"
					},
					{
						cover:"/static/ph.png",
						one1:"新盘",
						one2:"中骏丽景府二期",
						two:"晋江市 磁灶 | 建面97-143㎡",
						three:"7700",
						four:"在售",
						five:"住宅",
						six:"配套纯熟",
						seven:"公园",
						text1:"学府旁超万平绿化中骏大盘",
						text2:"预约看房，免费专车往返接送",
						flag:"false"
					},
					{
						cover:"/static/ph.png",
						one1:"新盘",
						one2:"中骏丽景府二期",
						two:"晋江市 磁灶 | 建面97-143㎡",
						three:"7700",
						four:"在售",
						five:"住宅",
						six:"配套纯熟",
						seven:"公园",
						text1:"学府旁超万平绿化中骏大盘",
						text2:"预约看房，免费专车往返接送",
						flag:"false"
					},
				]
			}
		},
		methods:{
			iconView(iview){
				iview.flag=!iview.flag
			}
			
		}
	}
</script>

<style>
</style>
