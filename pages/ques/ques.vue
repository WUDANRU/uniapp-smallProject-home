<template>
	<view>
		<view class="d-flex j-around w py-2 bd-white" style="height:100rpx;line-height:100rpx;position: fixed;z-index:100;">
			<view class="b-radius-circle px-2 py-5" style="height:40rpx;line-height:40rpx;" 
			v-for="(item,index) in qList" :key="index" @click="qclick(index,item)" :class="index===ex?'bcolor':'bd-1'">
				{{item.qtitle}}
			</view>
	</view>
	<scroll-view class="d-flex" scroll-y="true">
		<view class="">
			<view style="margin-top:140rpx;"></view>
			<view class="mx-2" v-for="(item2,index2) in qAll" :key="index2">
				<template>
				<c-qu :qt="qt" :qList="qList" :item2="item2"></c-qu>
				</template>
			</view>
			</view>
	</scroll-view>
	</view>
</template>

<script>
	import cQu from '@/components/cqu/cques.vue'
	export default {
		components:{
			cQu
		},
		data() {
			return {
				ex:0,
				qt:'精选',
				qList:[
					{
						qtitle:'精选',
					},
					{
						qtitle:'贷款',
					},
					{
						qtitle:'公积金',
					},
					{
						qtitle:'装修避坑',
					},
					{
						qtitle:'商业地产',
					}
				],
				qAll:[
					{
						text:'精选',
						qucover:'/static/ques.png',
						ancover:'/static/answer.png',
						jhcover:'/static/j-hua.png',
						title:'开便利店要如何选址？',
						main:'放哥说房',
						sec:'商业地产达人',
						fonts:'便利店店址选择，是以适应流向情况、人口分布，便利广大顾客购物为原则。在扩大销售的原则指导下,绝大多数商店等等等'
					},
					{
						text:'精选',
						qucover:'/static/ques.png',
						ancover:'/static/answer.png',
						jhcover:'/static/j-hua.png',
						title:'开便利店要如何选址？',
						main:'放哥说房',
						sec:'商业地产达人',
						fonts:'便利店店址选择，是以适应流向情况、人口分布，便利广大顾客购物为原则。在扩大销售的原则指导下,绝大多数商店等等等'
					},
					{
						text:'贷款',
						qucover:'/static/ques.png',
						ancover:'/static/answer.png',
						jhcover:'/static/j-hua.png',
						title:'开便利店要如何选址？',
						main:'放哥说房',
						sec:'商业地产达人',
						fonts:'便利店店址选择，是以适应流向情况、人口分布，便利广大顾客购物为原则。在扩大销售的原则指导下,绝大多数商店等等等'
					},
					{
						text:'贷款',
						qucover:'/static/ques.png',
						ancover:'/static/answer.png',
						jhcover:'/static/j-hua.png',
						title:'开便利店要如何选址？',
						main:'放哥说房',
						sec:'商业地产达人',
						fonts:'便利店店址选择，是以适应流向情况、人口分布，便利广大顾客购物为原则。在扩大销售的原则指导下,绝大多数商店等等等'
					},
					{
						text:'贷款',
						qucover:'/static/ques.png',
						ancover:'/static/answer.png',
						jhcover:'/static/j-hua.png',
						title:'开便利店要如何选址？',
						main:'放哥说房',
						sec:'商业地产达人',
						fonts:'便利店店址选择，是以适应流向情况、人口分布，便利广大顾客购物为原则。在扩大销售的原则指导下,绝大多数商店等等等'
					},
					{
						text:'公积金',
						qucover:'/static/ques.png',
						ancover:'/static/answer.png',
						jhcover:'/static/j-hua.png',
						title:'开便利店要如何选址？',
						main:'放哥说房',
						sec:'商业地产达人',
						fonts:'便利店店址选择，是以适应流向情况、人口分布，便利广大顾客购物为原则。在扩大销售的原则指导下,绝大多数商店等等等'
					},
					{
						text:'装修避坑',
						qucover:'/static/ques.png',
						ancover:'/static/answer.png',
						jhcover:'/static/j-hua.png',
						title:'开便利店要如何选址？',
						main:'放哥说房',
						sec:'商业地产达人',
						fonts:'便利店店址选择，是以适应流向情况、人口分布，便利广大顾客购物为原则。在扩大销售的原则指导下,绝大多数商店等等等'
					},
					{
						text:'商业地产',
						qucover:'/static/ques.png',
						ancover:'/static/answer.png',
						jhcover:'/static/j-hua.png',
						title:'开便利店要如何选址？',
						main:'放哥说房',
						sec:'商业地产达人',
						fonts:'便利店店址选择，是以适应流向情况、人口分布，便利广大顾客购物为原则。在扩大销售的原则指导下,绝大多数商店等等等'
					},
				],
			}
		},
		methods: {
			qclick(index,item){
				this.ex=index
				this.qt=item.qtitle
			}
		}
	}
</script>

<style>

</style>