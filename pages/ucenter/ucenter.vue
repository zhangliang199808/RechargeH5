<template>
  <div class="main">
    <div class="blue"></div>
    <div class="main_content">
      <div class="top">
        <div class="tx">
          <img v-if="log" src="../../static/img/tx.jpg" alt />
          <img v-if="name" :src="url" alt />
          <p v-if="name">{{username}}</p>
          <button class="btn" v-if="log" open-type="getUserInfo" @click="denglu()">登录</button>
          <!-- <button class="btn1" v-if="name" @click="tixian">提现</button> -->
        </div>
	
       <!-- <div class="wz">
          <div class="wz_left">
            <p>{{integral}}</p>
            <p>我的积分</p>
          </div>
          <div class="wz_center">
            <p>{{customer}}</p>
            <p>已免单(次)</p>
          </div>
          <div class="wz_right">
            <p>{{shop_num}}</p>
            <p>累计店铺(个)</p>
          </div>
        </div> -->
      </div>
	  <view class="toplist">
	  	<view @click="listtpye(index)" class="list" v-for="(item,index) in topList" :key="index">
	  		<image src="" mode="" style="display:block;width:90rpx;height:90rpx;background:#ccc;margin:0 auto"></image>
	  		<view class="listtext">
	  			{{item.name}}
	  		</view>
	  	</view>
	  </view>
      <div class="center" @click="paidui()">
        <!-- <div class="c_top">
          <img src="../../static/img/caidan.png" alt style="float: left;" />
          <p style="float: left;">积分订单</p>
          <img src="../../static/img/r_jiantou.png" alt style="float: right;" />
        </div> -->
        <!-- <div class="c_bottom">
          <img src="../../static/img/zd.png" alt style="float: left;" />
          <p style="float: left;">账单记录</p>
          <img src="../../static/img/r_jiantou.png" alt style="float: right;" />
        </div>-->
      </div>
      <!-- <div class="bottom" @click="xy()">
        <img src="../../static/img/kefu.png" alt style="float: left;" />
        <p style="float: left;">用户使用协议</p>
        <img src="../../static/img/r_jiantou.png" alt style="float: right;" />
      </div> -->
      <div @click="tuichu" class="bottom" v-if="log1">
        <img src="../../static/img/tc.png" alt style="float: left;" />
        <p style="float: left;">退出登录</p>
        <img src="../../static/img/r_jiantou.png" alt style="float: right;" />
      </div>
    </div>
    <Modal
      v-model="show"
      title="提示"
      text="确定登录吗？"
      cancel-text="暂不登录"
      confirm-text="立即登录"
      @cancel="cancel"
      @confirm="confirm"
      @event="event"
    ></Modal>
  </div>
</template>
<script>
import Modal from "@/components/x-modal/x-modal";
export default {
  components: { Modal },
  data() {
    return {
      canIUse: wx.canIUse("button.open-type.getUserInfo"),
      url: "",
      log: true,
      username: "",
      token: "",
      sex: "",
      integral: 0,
      customer: 0,
      shop_num: 0,
      state: "",
      log1: false,
      name: false,
      baseurl: "https://pd.qitusky.com",
      show: false,
	  topList: [{
	  			name:'收件地址',
	  		},
	  		{
	  			name:"我的留言"
	  		},
	  {name:"关于我们"},
	  {name:"优惠卷"},
	  {name:"订单记录"},
	  // {name:"快票儿"},
	  // {name:"网点地图"},
	  // {name:"业务办理"},
	  // {name:"电子发票"},
	  // {name:"电子发票"},
	  		],
    };
  },
  onLoad(options) {
    var that = this;
    // console.log(uni.getStorageSync("token"), 6666);
    // this.w()
    wx.getSetting({
      success(res) {
        // console.log(res, 3333);
        if (res.authSetting["scope.userInfo"]) {
          // 已经授权，可以直接调用 getUserInfo 获取头像昵称
          wx.getUserInfo({
            success: function(res) {
              // console.log(res, 55);
              that.url = res.userInfo.avatarUrl;
            }
          });
          // that.log1 = true;
          that.getdate();
        } else {
          console.log("没有授权");
          that.log = true;
          that.name = false;
          uni.removeStorage({
            key: "token",
            success: function(res) {
              // console.log(res, "success");
            }
          });
        }
      }
    });
    this.token = uni.getStorageSync("token");
    var that = this;
    wx.checkSession({
      success(res) {
        //session_key 未过期，并且在本生命周期一直有效
        // console.log(res, 999);
        // if(errCode = "0") {
        // 	uni.removeStorageSync('token')
        // }
      },
      fail(res) {
        // console.log(res, 888);
        // session_key 已经失效，需要重新执行登录流程
        // wx.login() //重新登录
      }
    });
    // that.w()
    // try {
    //   const res = uni.getStorageInfoSync();
    //   // console.log(res.keys);
    //   // console.log(res.currentSize);
    //   // console.log(res.limitSize);
    // } catch (e) {
    //   // error
    // }

    uni.getStorageInfo({
      success: function(res) {
        console.log(res.keys);
        if (res.keys.indexOf("token") > -1) {
          console.log("没有过期");
          //that.w();
          that.log = false;
          that.name = true;
          that.log1 = true;
          that.getdate();
        } else {
          // console.log(res.keys.indexOf("token"));
          that.log = true;
          that.name = false;
          that.log1 = false;
          console.log("登录过期");
        }
      }
    });

    // var token = uni.getStorageSync('token')
    //   if( token==null && token==''&& token==undefined) {
    // 		console.log('登录已过期')
    // 	}
    // console.log(token)

    wx.getUserInfo({
      success: function(res) {
        that.url = res.userInfo.avatarUrl;
        //  that.log = false;
        that.username = res.userInfo.nickName;
        // console.log(that.username, "wxd", that.url, "用户信息： ", that.openid);
      }
    });
    this.getdate();
  },
  onPullDownRefresh() {
    //监听下拉刷新动作的执行方法，每次手动下拉刷新都会执行一次
    // this.w();
    // setTimeout(function() {
    //   uni.stopPullDownRefresh(); //停止下拉刷新动画
    // }, 1000);
    this.getdate();
  },
  onShow() {
    // console.log(123);
    this.getdate();
  },
  methods: {
    getdate() {
      var that = this;
      uni.request({
        method: "post",
        url: this.baseurl + "/index/wxuser/isadd", //仅为示例，并非真实接口地址。
        header: {
          // 'custom-header': 'hello' //自定义请求头信息
        },
        data: {
          token: uni.getStorageSync('token')
        },
        success: function(res) {
          console.log(res, "数据");
          uni.hideLoading();
          if (res.data.recode != 100) {
            uni.showToast({
              title: res.data.remsg,
              icon: "none",
              duration: 2000
            });
          } else {
            that.integral = res.data.data[0].integral;
            that.customer = res.data.data[0].customer;
            that.shop_num = res.data.data[0].shop_num;
            that.state = res.data.data[0].user.state;
            // console.log(that.integral, "shuz");
          }
        },
        fail: function(err) {
          console.log(err, 123123123);
        }
      });
    },
    cancel(e) {
      console.log(e, "取消");
    },
    event(e) {
      console.log(e);
    },
    confirm(e) {
      // var that = this;
      console.log(e, "确认");
      this.login();
    },
    tuichu() {
      uni.removeStorageSync("token");
      this.log = true;
      this.log1 = false;
      this.name = false;
      this.integral = 0;
      this.customer = 0;
      this.shop_num = 0;
    },
    denglu() {
      // sc(item) {
      // this.$refs.xyDialog.show();
      // console.log(item);
      // this.id = item.id;
      this.show = true;
      // },
    },
    tixian() {
      if (this.state == 0) {
        uni.showToast({
          title: "请进行实名认证",
          icon: "none",
          duration: 2000,
          success: function() {
            uni.navigateTo({
              //里面是一个对象形式的参数
              // url:
              //   "cashout?url=" +
              //   this.url +
              //   "&username=" +
              //   this.username +
              //   "&integral=" +
              //   this.integral
              url: "certification"
            });
          }
        });
      } else {
        uni.navigateTo({
          //里面是一个对象形式的参数
          url:
            "cashout?url=" +
            this.url +
            "&username=" +
            this.username +
            "&integral=" +
            this.integral
          // url: "certification"
        });
      }
    },
    paidui() {
      console.log(111);
      if (uni.getStorageSync("token")) {
        // uni.navigateTo({
        //   //里面是一个对象形式的参数
        //   url: "check"
        // });
      } else {
        uni.showToast({
          title: "请登录！！！",
          icon: "none",
          duration: 2000
        });
      }
    },
    xy() {
      // uni.navigateTo({
      //   //里面是一个对象形式的参数
      //   url: "user"
      // });
    },
    bindGetUserInfo(e) {
      // console.log(e, 333);
    },
    login() {
      var that = this;
      // console.log(that.canIUse);

      wx.getUserInfo({
        success: function(res) {
          console.log(res);
          that.url = res.userInfo.avatarUrl;
          that.log = false;
          that.username = res.userInfo.nickName;
          that.sex = res.userInfo.gender;
          that.name = true;
          that.log1 = true;
          that.login1();
          console.log(1111);
        }
      });
    },
    login1() {
      var that = this;
      // uni.showToast({
      //   title: uni.getStorageSync("openid"),
      //   icon: "none",
      //   duration: 20000
      // });
      wx.request({
        method: "post",
        url: that.baseurl + "/index/Wxuser/login",
        header: {
          // 'custom-header': 'hello' //自定义请求头信息
        },
        data: {
          username: that.username,
          avatar: that.url,
          openid: uni.getStorageSync("openid"),
          sex: that.sex
        },
        success: function(res) {
          console.log(res, "登录成功");
          uni.setStorageSync("token", res.data.data[0].token);
          // console.log(that.username,'wxd',that.url, "13123 ");
          // that.getdate();

          //that.w();
          // uni.getStorageInfo({
          //   success: function(res) {
          //     console.log(res.keys);

          //     if (res.keys.indexOf("token") > -1) {
          //       console.log("没有过期");
          //       that.log = false;
          //       that.name = true;
          //       that.log1 = true;
          //       console.log(13);
          //     } else {
          //       console.log("登录过期");
          //       that.log = true;
          //       that.name = false;
          //       that.log1 = false;
          //     }
          //   }
          // });
        },
        fail: function(err) {
          console.log(err);
        }
      });
    },
	listtpye(id){
		console.log(id)
		if(id==0){uni.navigateTo({
		    url: '/pages/shdz/shdz'
		});}
		if(id==1){uni.navigateTo({
		    url: '/pages/liuYan/liuYan'
		});}
		if(id==2){uni.navigateTo({
		    url: '/pages/repair/repair'
		});}
		if(id==3){uni.navigateTo({
		    url: '/pages/youhuij/youhuij'
		});}
		if(id==4){uni.navigateTo({
		    url: '/pages/ddjl/ddjl'
		});}
		// if(id==5){uni.navigateTo({
		//     url: '/pages/heating/heating'
		// });}
		// if(id==6){uni.navigateTo({
		//     url: '/pages/heating/heating'
		// });}
		// if(id==7){uni.navigateTo({
		//     url: '/pages/ywbl/ywbl'
		// });}
		console.log(12)
		// uni.navigateTo({
		//     url: '/pages/heating/heating'
		// });
	},
  }
};
</script>

<style>
@import url("../../static/fonts/iconfont.css");
page{
	background: #f1f1f1 !important;
}
.main {
  width: 100%;
  height: 100%;
  background-color: #000;
  position: relative;
}

.blue {
  width: 100%;
  height: 350rpx;
  background-image: linear-gradient(to right, #677eff, #53b0fe);
  position: absolute;
  top: 0;
  left: 0;
}
.main_content {
  width: 90%;
  height: 80%;
  position: absolute;
  background-color: transparent;
  top: 100rpx;
  left: 0;
  right: 0;
  margin: auto;
  /* overflow: hidden; */
}
.top {
  width: 100%;
  height: 320rpx;
  background-color: #fff;
  border-radius: 20rpx;
  box-shadow: 0px 6rpx 10rpx #ccc;
  padding: 30rpx;
  box-sizing: border-box;
}
.top .tx {
  width: 100%;
  height: 50%;
  background-color: #fff;
  border-radius: 20rpx 20rpx 0px 0px;
  display: flex;
  position: relative;
}
.top .tx img {
  width: 100rpx;
  height: 100rpx;
  border-radius: 50%;
  float: left;
}
.top .tx p {
  float: left;
  margin-left: 40rpx;
  margin-top: 30rpx;
  font-weight: 700;
}
.top .wz {
  width: 100%;
  height: 50%;
  background-color: #fff;
  border-radius: 0px 0px 20rpx 20rpx;
  display: flex;
  flex-direction: row;
  text-align: center;
}
.top .wz .wz_left {
  flex: 1;
}
.top .wz .wz_left :nth-child(1),
.top .wz .wz_center :nth-child(1),
.top .wz .wz_right :nth-child(1) {
  font-size: 40rpx;
  color: #86cee9;
  margin-top: 20rpx;
}
.top .wz .wz_left :nth-child(2),
.top .wz .wz_center :nth-child(2),
.top .wz .wz_right :nth-child(2) {
  font-size: 24rpx;
  color: #d2d2d4;
  margin-top: 20rpx;
}
.top .wz .wz_center {
  flex: 1;
  border-left: 1px solid #f5f5f5;
  border-right: 1px solid #f5f5f5;
}
.top .wz .wz_right {
  flex: 1;
}
.center {
  width: 100%;
  height: 100rpx;
  margin-top: 40rpx;
  background-color: #fff;

  box-sizing: border-box;
  overflow: hidden;
}
.center i {
  display: block;
  color: #a4e3ff;
  font-size: 36rpx;
}
.center p {
  float: left;
  margin-left: 40rpx;
  font-size: 30rpx;
  color: #999;
}
.center .c_top {
  width: 100%;
  /* height: 50%; */
  padding: 0 30rpx;
  background-color: #fff;
  /* border-bottom: 1px solid #f5f5f5; */
  line-height: 100rpx;
  cursor: pointer;
  box-sizing: border-box;
}
.center img,
.bottom img {
  width: 40rpx;
  height: 40rpx;
  margin-top: 30rpx;
}
.center .c_bottom {
  width: 100%;
  height: 50%;
  padding: 0 30rpx;
  background-color: #fff;
  line-height: 100rpx;
  border-bottom: 1px solid #f5f5f5;
  cursor: pointer;
  box-sizing: border-box;
}
.bottom {
  width: 100%;
  height: 100rpx;
  margin-top: 40rpx;
  background-color: #fff;
  line-height: 100rpx;
  padding: 0 30rpx;
  box-sizing: border-box;
}
.bottom i {
  display: block;
  color: #a4e3ff;
  font-size: 36rpx;
}
.bottom p {
  float: left;
  font-size: 30rpx;
  margin-left: 40rpx;
  color: #999;
}

.btn {
  float: left;
  width: 140rpx;
  height: 65rpx;
  background: rgba(0, 0, 0, 0);
  /* border-radius: 60rpx; */
  border: 1px solid rgba(0, 0, 0, 0);
  line-height: 65rpx;
  padding: 5rpx;
  text-align: center;
  margin-left: 40rpx;
  margin-top: 30rpx;
  font-size: 30rpx;
  font-weight: 700;
}
.btn1 {
  float: right;
  width: 140rpx;
  height: 65rpx;
  /* background: rgba(0, 0, 0, 0); */
  background-color: #fafafa;
  /* border-radius: 60rpx; */
  border: 1px solid rgba(0, 0, 0, 0);
  line-height: 65rpx;
  padding: 5rpx;
  text-align: center;
  /* margin-left: 40rpx;
  margin-top: 30rpx; */
  position: absolute;
  top: 28rpx;
  right: 30rpx;
  font-size: 30rpx;
  font-weight: 700;
}

.clearfix:after {
  /*伪元素是行内元素 正常浏览器清除浮动方法*/
  content: "";
  display: block;
  height: 0;
  clear: both;
  visibility: hidden;
}
.toplist{
		display:flex;
		flex-wrap:wrap;
		margin-top:40rpx;
		background:#fff;
		border-radius:15rpx;
		padding:10rpx 0;
	}
	.list{
		width:25%;
		margin:30rpx 0
	}
	.listtext{
		text-align:center;
		font-size:20rpx;
		margin-top:10rpx
	}
</style>
