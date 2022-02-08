<template>
  <view class="page-login">
    <view v-if="canIUse||canIGetUserProfile">
      <view class='content'>
        <image style="width: 140rpx; height: 140rpx;" mode="aspectFit" src="/static/wx.jpg"></image>
        <view class="name">登录</view>
        <view>申请获取以下权限</view>
        <text>获得你的公开信息(昵称、头像、地区等)</text>
      </view>

      <view class="login-box">
        <!--新版登录方式-->
        <button v-if="canIGetUserProfile" class='login-btn' type='primary' @click="bindGetUserInfo"> 授权登录 </button>
        <!--旧版登录方式-->
        <button v-else class='login-btn' type='primary' open-type="getUserInfo" withCredentials="true" lang="zh_CN" @getuserinfo="bindGetUserInfo"> 授权登录 </button>

      </view>
    </view>
    <view v-else class="text-center">
      请升级微信版本
    </view>

  </view>
</template>
<script>
export default {
  data () {
    return {
      canIUse: uni.canIUse('button.open-type.getUserInfo'),
      canIGetUserProfile: false,//微信登录新旧版本 true是新
    }
  },
  onLoad () {
    //必须先调用微信的登录接口 然后再去调用授权拿微信个人信息（否则顺序错乱会导致 小概率授权后拿不到头像和昵称）
    this.wxLogin()
    var _this = this
    if (uni.getUserProfile) {
      this.canIGetUserProfile = true
    }
  },
  onShow () {

  },
  methods: {
    //登录授权
    bindGetUserInfo (e) {
      console.log('e', e)
      var _this = this
      if (this.canIGetUserProfile) {
        //新版登录方式
        uni.getUserProfile({
          desc: '获取您个人信息用于登录！',
          success: (res) => {
            console.log('用户信息', res)
            // 存入个人信息
            uni.setStorageSync('userInfo_winxin', res.userInfo)
            _this.updateUserInfo()
          },
          fail: (res) => {
            console.log(res)
          }
        })
      } else {
        //旧版登录方式 --自动就拉起授权窗口
        if (e.detail.userInfo) {
          //用户按了允许授权按钮
          //console.log('手动');
          console.log('老版用户信息', e.detail.userInfo)
          // 存入个人信息
          uni.setStorageSync('userInfo_winxin', e.detail.userInfo)
          _this.updateUserInfo()
        } else {
          console.log('用户拒绝了授权')
          //用户按了拒绝按钮
        }
      }
    },
    //登录---目的拿到code
    wxLogin () {
      let _this = this
      // 获取登录用户code
      uni.login({
        provider: 'weixin',
        success: function (res) {
          console.log(res);
          if (res.code) {
            //将用户登录code传递到后台置换用户SessionKey、OpenId等信息 可参照此篇文章： https://ask.dcloud.net.cn/article/37452
            // 1.拿code调后端接口1 也就是getOpenid() 换取到SessionKey、OpenId(这个是唯一且固定不变)
            // 2.拿openId 调后端自己写的登录接口2  获取到cookie等信息 （这个cookie后期请求放在请求头上的） 登陆成功进行存储和跳转页面

            //这是我们的后端接口1--换取到SessionKey、OpenId
            // let params = { code: res.code}
            // getOpenid(params, false).then((res) => {
            //   console.log('拿code调后端接口1 换取到SessionKey、OpenId', res)
            //   uni.setStorageSync('session_key', res.data.session_key)
            //   uni.setStorageSync('openid', res.data.openid)
            // })
          } else {
            uni.showToast({ title: '获取logon_code失败', duration: 2000 })
            console.log('获取logon_code失败' + res.errMsg)
            _this.wxLogin()
          }
        },
        fail: (res) => {
          uni.showToast({ title: '获取logon_code失败', duration: 2000 })
          console.log('获取logon_code失败' + res.errMsg)
          _this.wxLogin()
        }
      })
    },
    //向后台更新信息
    updateUserInfo () {
      let _this = this

      //这是我们的后端接口2--登录接口2  获取到cookie等信息（这个cookie后期请求放在请求头上的）
      // let params = {
      //   openid: uni.getStorageSync('openid'),
      //   nickname: uni.getStorageSync('userInfo_winxin').nickName,
      //   head_image: uni.getStorageSync('userInfo_winxin').avatarUrl,
      // }
      // loginByWechat(params).then((res) => {

      // })

      //下面的这个cookie键值对是暂时写死的，正常应该接口2返回的
      let login_cookie_name = 'login_cookie_name'
      let login_cookie_value = 'login_cookie_value'
      uni.setStorageSync('login_cookie_name', login_cookie_name)
      uni.setStorageSync('login_cookie_value', login_cookie_value)
      // 注意：以上的存储为了在request请求时候携带和判断用  在退出登录时候需要清除掉

      uni.hideLoading()
      uni.showToast({
        title: '接口登录逻辑自写-登陆成功',
        duration: 1500,
        icon: 'success',
      })
      // 跳转到首页
      uni.reLaunch({ url: '/pages/index/index' })

    }
  }
}
</script>

<style lang="less" scoped>
.content {
  text-align: center;
}
</style>