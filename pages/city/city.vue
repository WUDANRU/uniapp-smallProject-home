<template>
	<view>
		<!-- <!-- @confirm="a"，input框点击enter触发 -->
		<view class="bd-9 w bd-white d-flex align-c" style="height:80rpx;">
			<input ref="input" @input="cliInput" v-model="val" class="b-radius-2 my-1 mx-2 d-flex px-2"  placeholder-class="iconfont icon-sousuo"
			 style="flex:1;height:60rpx;line-height:60rpx;background:#fff;color:#979b9e;" placeholder="请输入城市名" />
			<text v-if="!isVal" @click="iconCli" style="color:#979b9e;" class="iconfont icon-qingchu"></text>
			 <view v-if="!isVal" class="mx-2" @click="delCli">
			 	取消
			 </view>
		</view>
		<view class="" v-if="arr.length===0 && isVal">
		<scroll-view scroll-y :scroll-top="rightScrollTop" style="height:2000rpx;">
		<view class="">
		
		<view class="pt-a"></view>
		
		<view class="mx-2">
			<view class="">
				<view class="c-8">定位/历史</view>
				<view class="mt-3 border-5 py-1 d-flex j-center" style="width:180rpx;">
				 <text style="font-size:24rpx;margin-top:5rpx;" class="iconfont icon-dingwei"></text>
				 <text>{{ci}}</text>
				</view>
			</view>
			<view class="mt-4" style="">
				<view class="c-8">热门</view>
				<view class="d-flex f-r" style="flex-wrap: wrap;">
				<view style="width:180rpx;" class="d-flex j-center mr-2 mt-2 px-1 py-1 border-5" v-for="(item,index) in hot" :key="index">
					{{item.city}}
				</view>
				</view>
			</view>
			</view>
			
		</view>
		
		<view class="mx-2 mt-6">
			<view class="left-item" v-for="(i,k) in history" :key="k">
			<view class="mt-3 c-8">
				{{i.idx}}
			</view>
			<view class="border-4 mt-3"></view>
			<block v-for="(i1,k1) in i.cities" :key="k1">
				<view class="mt-3" @click.stop="clicked(i1.city_name)">{{i1.city_name}}</view>
				<view class="mt-3 border-4"></view>
			</block>
			</view>
		</view>
		</scroll-view>
		
		<view class="p-fixed mr-1" style="top:300rpx;right:0;">
			<view style="width:50rpx;" class="d-flex f-c j-center align-c">
				<view class="c-8 font-1a mb-2">
					历史热门
				</view>
				<view @click="cliIdx(item1.idx,index1)" class="mb-1 font-2 c-8" v-for="(item1,index1) in indexAll" :key="index1"
				 >{{item1.idx}}</view>
			</view>
		</view>
	</view>	
	<view class="" v-if="arr.length!==0">
		<view class="mx-3" v-for="(v,vv) in arr" :key="vv">
			<view @click="itemCli(v)" style="height:80rpx;line-height:80rpx;">
				{{v}}
			</view>
			<view class="border-5"></view>
		</view>
	</view>
	
	</view>
</template>

<script>
	import { list,index } from '@/common/index.list.js';
	export default {
		data() {
			return {
			hot:[
				{
					city:'上海'
				},
				{
					city:'广州'
				},
				{
					city:'深圳'
				},
				{
					city:'北京'
				},
				{
					city:'成都'
				},
				{
					city:'南京'
				},
				{
					city:'天津'
				},
				{
					city:'杭州'
				},
				{
					city:'郑州'
				}
			],
			history:[],
			indexAll:[],
			rightScrollTop:0,
			cateItemHeight:0,
			leftDomsTop:[],
			arr:[],
			timer:null,
			isVal:true,
			val:'',
			ci:'地区',
			}
		},
		onReady(){ //onReady,mounted都是加载完成
				const query = uni.createSelectorQuery().in(this)
				query.selectAll('.left-item').fields({
					size: true,
					rect: true
				}, data => { //获取节点的相关信息
					this.leftDomsTop = data.map(v => {
						// console.log(v.height,'v.height')
						this.cateItemHeight = v.height
						return v.top //(每个)节点离页面顶部的距离
					})
					// console.log(this.leftDomsTop, 'left')
				}).exec()
		},
		onLoad(){
			this.history=list
			this.indexAll=index
		this.ci=JSON.parse(uni.getStorageSync('dingwei'))
		},
		methods: {
			cliInput(e) {
						  clearTimeout(this.timer)
						  this.timer = setTimeout(() => {
						    this.getSearch(e)
						  }, 500)
						},
			getSearch(e){
				this.val=e.detail.value
				if(this.val.length!==0){ //有值
				this.isVal=false	
				}else{
				this.isVal=true	
				}
				let data=[]
				for(let i=0;i<this.history.length;i++){
					for(let j=0;j<this.history[i].cities.length;j++){
						// console.log(this.history[i].cities[j].city_name,'h')
						data.push(this.history[i].cities[j].city_name)
						}}
						console.log(data,'data')
					this.arr=data.filter(item=>item.includes(this.val))
					// console.log(this.arr.length,'gg')
		},
		iconCli(){
			// this.$refs.input.value='' //这个会报错，获取dom //console.log(this.$refs.input.value,'input')
			this.val=''
		},
		delCli(){
			this.isVal=true	
		},
		itemCli(v){
			uni.switchTab({
				url:'/pages/index/index'
			})
			uni.$emit('clicked',v)
		},
		clicked(item){
			uni.switchTab({
				url:'/pages/index/index'
			})
			uni.$emit('clicked',item)
		},
		cliIdx(item1,index1){
			// console.log(item1,index1,'index1')
			// console.log(this.leftDomsTop[index1],'定位')
			this.rightScrollTop=this.leftDomsTop[index1]-80
		},
		}
	}
</script>

<style>
	uni-scroll-view{
		overflow: none!important;
	}
/* 解决小程序和app滚动条的问题 */
/* #ifdef MP-WEIXIN || APP-PLUS */
	::-webkit-scrollbar{
	    display: none;
	}
/* #endif */
/* 解决H5 的问题 */
/* #ifdef H5 */
    uni-scroll-view .uni-scroll-view::-webkit-scrollbar {
    	/* 隐藏滚动条，但依旧具备可以滚动的功能 */
	display: none
    }
/* #endif */
</style>
