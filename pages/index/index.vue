<template>
	<view class="">
	<view class="h bcolor d-flex f-r align-c px-3">
		<image src="/static/logo.png" style="width:140rpx;" mode="widthFix"></image>
		<view class="ml-2 bd-white d-flex px-1" style="flex:1;height:80rpx;line-height:80rpx;border-radius:10rpx;color:#767b81;">
			<view @click="naviCli">
				<!-- width:50px;overflow: hidden; text-overflow: ellipsis; white-space: nowrap; background:orange; -->
				<view style="display:inline-flex;">{{city}}</view>
				<text style="font-size:28rpx;" class="ml-1 iconfont icon-xiajiantou mr-2"></text>
			</view>
			<navigator url="/pages/seroom/seroom">
			<view class="pl-1 c-8 font-2" style="flex:1;">安心挑好房，当然安居客</view>
			</navigator>
		</view>
		<button open-type="contact" class="bcolor" style="width:70rpx;height:60rpx;line-height:60rpx;">
			<text style="font-size:45rpx;" class="c iconfont icon-wodekefu">
			</text>
		</button>
	</view>
<scroll-view scroll-x class="my-3a" style="margin:0;">
		<view class="d-flex f-r">
		<view class="" v-for="(b,u) in 2" :key="u">
			<view class="pl-1 py-2 d-flex f-r flex-wrap" style="width:750rpx;">
			<view class="d-flex f-c py-1 px-2 align-c" v-for="(a,i) in icons" :key="i">
			<image style="width:100rpx;height:100rpx;" :src="a.cover" mode="widthFix" />
			<view class="">
				{{a.title}}
			</view>
			</view>
			</view>
			
			<!-- <view style="background:pink;width:750rpx;">
			aaaaaa	
			</view> -->
		</view>
		</view>
	</scroll-view>
		<view class="mx-2">
	<view class="d-flex w align-c" style="height:160rpx;">
		<view class="mr-2">
			<view class="c-3 c-9">
				{{cityName}}
			</view>
			<view class="border-6 my-1" style="width:140rpx;">
			</view>
			<view class="c-3">
				房价
			</view>
		</view>
		<view class="d-flex f-r j-around" style="flex:1;">
			
			<view class="c-3">
				<!-- align-self:stretch; -->
				<view class="">
				<text class="font-4 c-4 mr-2 letter-s-1">15134</text>元
				</view>
				<view class="">
					最新均价
				</view>
			</view>
			
			<view class="c-3">
				<view class="">
					<text class="font-4 c-4 letter-s-2">0.47%</text>
				</view>
				<view class="">
					比上月
				</view>
			</view>
			
			<view class="c-3">
				<view class="font-4 c-4 letter-s-2">
					<text>18.55%</text>
				</view>
				<view class="">
					比去年
				</view>
			</view>
			
		</view>
	</view>
	
	<view class="d-flex j-center">
		<image src="/static/news.png" style="width:690rpx;" mode="widthFix"></image>
	</view>
	<scroll-view class="my-3a" scroll-x>
		<view class="d-flex f-r">
	
		<view v-for="(i,k) in scroller" :key="k" class="px-2 py-2 b-radius mr-1a" :style="i.style">
			<view class="">
				{{i.area}}
			</view>
			<view class="my-1 font-1a" :style="i.color">
				{{i.text}}
			</view>
			<view class="d-flex">
				<image :src="i.img1" style="width: 138rpx;" mode="widthFix"></image>
				<image :src="i.img2" style="width: 138rpx;" mode="widthFix" class="ml-1a"></image>
			</view>
		</view>
		
		</view>
	</scroll-view>

	<template>
		<c-like></c-like>
	</template>
	
	</view>
	</view>
</template>

<script>
	import cLike from '@/components/clike/clike.vue'
	export default {
		components:{
			cLike
		},
		data() {
			return {
				city:'地区',
				cityName:'地区',
				icons:[
					{
					cover:'/static/tabbar/icon.png',
					title:'新房'	
					},
					{
					cover:'/static/tabbar/icon.png',
					title:'新房'	
					},
					{
					cover:'/static/tabbar/icon.png',
					title:'新房'	
					},
					{
					cover:'/static/tabbar/icon.png',
					title:'新房'	
					},
					{
					cover:'/static/tabbar/icon.png',
					title:'新房'	
					},
					{
					cover:'/static/tabbar/icon.png',
					title:'新房'	
					},
					{
					cover:'/static/tabbar/icon.png',
					title:'新房'	
					},
					{
					cover:'/static/tabbar/icon.png',
					title:'新房'	
					},
					{
					cover:'/static/tabbar/icon.png',
					title:'新房'	
					},
					{
					cover:'/static/tabbar/icon.png',
					title:'新房'	
					},
				],
			scroller:[
				{
					area:"特价房专区",
					text:"好而不贵 特价好房源",
					img1:"/static/room-a.png",
					img2:"/static/room-b.png",
					style:"background:#faf8f5;",
					color:"color:#a7874d;"
				},
				{
					area:"特价房专区",
					text:"好而不贵 特价好房源",
					img1:"/static/room-a.png",
					img2:"/static/room-b.png",
					style:"background:#f9f7f8;",
					color:"color:#bb898a;"
				},
				{     
					area:"特价房专区",
					text:"好而不贵 特价好房源",
					img1:"/static/room-a.png",
					img2:"/static/room-b.png",
					style:"background:#f3f7f9;",
					color:"color:#55a3b7;"
				},
			],
		
			}
		},
		watch:{
		city(newValue,oldValue){
		if(newValue.length>3){
			let n=newValue.slice(0,1)
			let last=newValue.slice(newValue.length-1,newValue.length)
			this.city=`${n}`+`...`+`${last}`
		}},
		},
		onLoad(){
			uni.$on('clicked',(e)=>{
				this.city=e
				this.cityName=e
			})
		},
		onUnload(){
			uni.$off('clicked')
		},
		onShow() {
		   this.getAuthorizeInfo()
		},
		methods: {
			// 位置授权
			getAuthorizeInfo(){
			    // const that = this
			    uni.authorize({ //authorize scope.userLocation需要在app.json(manifest.json)中声明permission字段
			        scope: 'scope.userLocation',
			        // success() {
			        // 	// 允许授权
			        //     that.getLocationInfo()
			        // },
			        // fail(){    
			        // 	// 拒绝授权
			        //     that.openConfirm()
			        //     console.log("你拒绝了授权，无法获得周边信息")
			        // }
					success:()=>{
						// 允许授权
					    this.getLocationInfo()
					},
					fail:()=>{    
						// 拒绝授权
					    this.openConfirm()
					    console.log("你拒绝了授权，无法获得周边信息")
					}
			    })
			},
			// 获取地理位置
			getLocationInfo(){  
			    uni.getLocation({
			        type: 'wgs84',
					success:(res)=>{
							   // console.log(res,'res')
												uni.request({
												/* 这个url拿去直接用，是腾讯官方api，字段key需要更改为自己的 */
													url: 'https://apis.map.qq.com/ws/geocoder/v1/', //逆地址解析
													data: {
														location: res.latitude + ',' + res.longitude,
														key: 'CPEBZ-FD7CS-3AZOO-6KV2W-AN4IT-M7BN4',
														get_poi: 1
													},
													success: (result) => {
													// console.log(result,result.data.result.address_component.city,'result')
													let t=result.data.result.address_component.city
													if(!t){
														return
													}
													this.city=t	
													this.cityName=t
												uni.setStorageSync('dingwei',JSON.stringify(t))
													},
						})
				}
			    })
			},
			// 再次获取授权。当用户第一次拒绝后再次请求授权
			openConfirm(){
			    uni.showModal({
			        title: '请求授权当前位置',
			        content: '需要获取您的地理位置，请确认授权',
			        success: (res)=> {
			            if (res.confirm) {
			                uni.openSetting()// 打开地图权限设置
			            } else if (res.cancel) {
			                uni.showToast({
			                    title: '你拒绝了授权，无法获得周边信息',
			                    icon: 'none',
			                    duration: 1000
			                })
			            }
			        }
			    })
			},
			naviCli(){
				uni.navigateTo({
					url:'/pages/city/city'
				})
			},
		}
	}
</script>

<style>
	button:after,uni-button:after{
		border:none!important;
	}
</style>
