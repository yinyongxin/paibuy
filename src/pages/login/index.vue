<template>
  <view class="login">
    <uv-image width="60px" height="60px" src="https://cdn.uviewui.com/uview/album/1.jpg" :radius="8"></uv-image>
    <view class="formContent">
      <view class="content">
        <view class="duanxin">
          <uv-input placeholder="请输入内容" border="surround" v-model="formData.phone"></uv-input>
          <uv-input placeholder="后置插槽">
            <!-- vue3模式下必须使用v-slot:suffix -->
            <template v-slot:suffix>
              <uv-code ref="uCode" @change="codeChange" seconds="20" changeText="X秒重新获取哈哈哈"></uv-code>
              <uv-button @click="getCode" :text="tips" type="success" size="mini"></uv-button>
            </template>
          </uv-input>
        </view>
      </view>
    </view>

    <view>
      <uv-divider text="其他登陆方式"></uv-divider>
      <uv-row justify="center">
        <uv-col span="3">
          <uv-icon label="微信" labelPos="bottom" color="green" space="8rpx" name="weixin-circle-fill"
            size="32"></uv-icon>
        </uv-col>
        <uv-col span="3">
          <uv-icon label="密码" labelPos="bottom" space="8rpx" name="lock-fill" size="32"></uv-icon>
        </uv-col>
      </uv-row>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      /**
       * 方式
       * passworod
       * default
       * weixin
       */
      type: 'passworod',
      tips: '',
      value: '内容',
      formData: {
        phone: ''
      }
    }
  },
  methods: {
    codeChange(text) {
      this.tips = text;
    },
    getCode() {
      if (this.$refs.uCode.canGetCode) {
        // 模拟向后端请求验证码
        uni.showLoading({
          title: '正在获取验证码'
        })
        setTimeout(() => {
          uni.hideLoading();
          // 这里此提示会被this.start()方法中的提示覆盖
          uni.showToast({
            title: '验证码已发送'
          });
          // 通知验证码组件内部开始倒计时
          this.$refs.uCode.start();
        }, 2000);
      } else {
        uni.showToast({
          title: '倒计时结束后再发送'
        });
      }
    },
    change(e) {
      console.log('change', e);
    }
  }
}
</script>

<style lang="scss">
.login {
  padding: 24rpx;
  padding-top: 120rpx;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  height: 100vh;
  box-sizing: border-box;

  >* {
    width: 100%;
  }

  .formContent {
    flex: 1;

    .content {
      margin: 0 48rpx;
      margin-top: 140rpx;
    }

    .duanxin {
      display: flex;
      flex-direction: column;
      gap: 24rpx;
    }
  }
}
</style>
