<template>
	<view>
		<view v-for="(item,index) in iconAll" :key="index">
			<view class="" v-for="(item2,index2) in item" :key="index2">
				{{item2}}
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
			iconAll:[[
				{cover:'/static/tabbar/icon.png',
					title:'新房',
					},
				{cover:'/static/tabbar/icon.png',
					title:'新房'},
			],[
				{cover:'/static/tabbar/icon.png',
					title:'新房'},
				{cover:'/static/tabbar/icon.png',
					title:'新房'},
			]]	
			}
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
