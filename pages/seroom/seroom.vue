<template>
	<view>
	<view class="d-flex f-r align-c px-2 py-1a">
		<view class="d-flex align-c bd-7 mr-1a b-radius-2" style="flex:1;height:80rpx;line-height: 80rpx;">
			<view @click="show=!show">
				<text class="c-7 pl-2">{{seText}}</text>
				<text style="font-size:8rpx;" class="pl-1 c-8 iconfont icon-xiajiantou"></text>
			</view>
			<input class="pl-2" placeholder-class="c-8 font-2a" placeholder="请输入楼盘名称和地址" />
		</view>
		<view class="c-7 px-1 py-1" @click="urlClick">
			取消
		</view>
	</view>
	<view class="border-4"></view>
	
	<view class="px-2">
		<view class="mt-3 c-7">
			热门搜索
		</view>
		<view class="d-inline-flex f-r" v-for="(item,index) in hotList" :key="index">
			<view class="b-radius-2 c-8 font-2a bd-8 m-sm px-1 py-1">
				{{item.text}}
			</view>
		</view>
	</view>
	
	<view  style="position: fixed;top:140rpx;left:-60rpx;" :style="show?'display:flex;':'display:none;'">
		<view class="a"></view>
	<view class="b" style="">
		<view @click="seText='新房'" :class="seText==='新房'?'c-8 bd-7':''" style="height:75rpx;line-height: 75rpx;text-align:center;">
			搜新房
		</view>
		<view @click="seText='二手房'" :class="seText==='二手房'?'c-8 bd-7':''" style="height:75rpx;line-height: 75rpx;text-align:center;">
			搜二手房
		</view>
	</view>
	</view>
	
	</view>
</template>

<script>
	export default {
		data() {
			return {
			show:false,
			seText:'新房',
			hotList:[
				{
					text:"配套成熟"
				},
				{
					text:"南湖"
				},
				{
					text:"富门花园"
				},
				{
					text:"近地铁"
				},
				{
					text:"番禺"
				},
				{
					text:"祈福黄金海岸(别墅)"
				}
			]
			}
		},
		methods: {
		urlClick(){
			uni.switchTab({
				url:'/pages/index/index'
			})
		}	
		}
	}
</script>

<style>
	    .a{
		  position:absolute;
		  margin-top:24rpx;
	      margin-left:120rpx;
	      display: inline-flex;
	      width: 0;
	      height: 0;
	      border-style: solid;
	      border-width: 16rpx;
	      border-color: #fff;
	      transform: rotate(-45deg);
	      box-shadow: 2px -2px 2px #d5dedb;
		  /* z-index:100; */
	    } 
		.b{
			position:relative;
			box-shadow: 0 3px 4px 0 #d5dedb;
			margin-top:34rpx;
			margin-left:90rpx;
			width:230rpx;
			background:#fff;
			border: 1px solid #d5dedb;
		}
</style>
