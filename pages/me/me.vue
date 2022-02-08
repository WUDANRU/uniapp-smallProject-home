<template>
	<view>
		<view class="w bcolor" style="height:300rpx;"></view>
		<view class="mx-4 bd-white" style="box-shadow: 0 3px 4px 0 #d5dedb;width:670rpx;height:360rpx;position: absolute;top:30rpx;">
			<view class="d-flex align-c f-r mx-3 mt-4 mb-4">
				<image src="/static/user.png" style="width: 150rpx;" mode="widthFix"></image>
				<view class="ml-2" style="">
					<view class="font-4">
						注册/登录
					</view>
					<view class="font-2a mt-1 f-r d-flex" style="">
							登录后即可体验更多服务 > 
						 <!-- <view style="margin-top:40rpx;font-size:40rpx;color:#a2a2a2;" class="iconfont icon-jiantou_liebiaoxiangyou"></view> -->
					</view>
				</view>
			</view>
			<view class="d-flex j-around" style="text-align: center;">
				<view class=""  v-for="(u,ux) in 3" :key="ux">
					<view class="">
						2
					</view>
					<view class="">
						浏览历史
					</view>
				</view>
				
			</view>
		</view>
		<view style="margin-top:108rpx;"></view>
		<view class="mx-4 mt-2">
			<view class="mb-2 font-4">
				房产服务
			</view>
			<view class="d-flex f-r">
				<block v-for="(item,index) in iconAll" :key="index">
				<view class="mr-5" style="text-align: center;">
					<text :class="item.icon" style="font-size:50rpx;"></text>
					<view class="font-2">{{item.text}}</view>
				</view>
				</block>
			</view>
			<view class="d-flex mt-2 f-c" style="height:100rpx;line-height:100rpx;" v-for="(i,ex) in textAll" :key="ex">
				<view class="d-flex j-sb">
					<text>{{i.title}}</text>
					<text style="font-size: 55rpx;color:#d8d8d8;" class="iconfont icon-jiantou_liebiaoxiangyou"></text>
				</view>
				<view class="border"></view>
			</view>
		</view>	
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				iconAll:[
					{
						icon:'iconfont icon-fangwuzixun',
						text:'看房管理'
					},
					{
						icon:'iconfont icon-fangwufangchan',
						text:'卖房管理'
					},
				],
				textAll:[
					{
						title:'账号设置'
					},
					{
						title:'在线客服'
					},
					{
						title:'关注公众号'
					},
				]
			}
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
