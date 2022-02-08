<template>
	 <view class="d-flex align-c f-c j-center" style="transform: scale(1.2);">
		
		<view v-if="videoPlay">
		 <video
		     controls
		     id="myvideo"
		     :src="videoUrl"
		     @fullscreenchange="screenChange"
		  ></video>
		</view>
		
	</view> 
</template>

<script>
	export default {
		data() {
			return {
				videoPlay: true,
				videoUrl: 'https://vd2.bdstatic.com/mda-jm38zndgehisax4v/sc/mda-jm38zndgehisax4v.mp4?playlist=%5B%22hd%22%2C%22sc%22%5D&v_from_s=hkapp-haokan-hna&auth_key=1641666364-0-0-039a11795f1c60ea98e04ebf2fbd56eb&bcevod_channel=searchbox_feed&pd=1&pt=3&logid=3364459243&vid=11929476586695670866&abtest=&klogid=3364459243'
			}
		},
		methods: {
			screenChange(e) {
			  let fullScreen = e.detail.fullScreen; // 值true为进入全屏，false为退出全屏
			  console.log(e, "全屏");
			  if (!fullScreen) {
			    //退出全屏
			    this.videoPlay = false;   // 隐藏播放盒子
			  }
			},
			// 触发全屏播放的点击事件
			videoShow(item) {
			  this.videoContext = uni.createVideoContext("myvideo", this);    // this这个是实例对象 必传
			  console.log(item,'item')
			  this.videoUrl = item.video_path;
			  this.videoContext.requestFullScreen({ direction: 90 });  
			  this.videoContext.play();
			  this.videoPlay = true;  // 显示播放盒子
			},
		}
	}
</script>

<style>
	page{
		width:750rpx;
		height:100%;
		display:flex;
		justify-content:center;
		align-items:center;
		position: fixed;
		top:0;
		bottom:0;
		left:0;
		right:0;
		background: #000201;
	}
</style>