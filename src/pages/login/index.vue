<template>
  <view class="login">
    <view>
      <uv-image width="80px" height="80px" src="https://cdn.uviewui.com/uview/album/1.jpg" :radius="8"></uv-image>
    </view>
    <view>
      <uv-divider text="分割线"></uv-divider>
      <uv-row justify="center" customStyle="margin-bottom: 10px">
        <uv-col span="3">
          <uv-icon name="weixin-circle-fill" size="40"></uv-icon>
        </uv-col>
        <uv-col span="3">
          <uv-icon name="weixin-circle-fill" size="40"></uv-icon>
        </uv-col>
      </uv-row>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      title: 1
    }
  },

}
</script>

<style lang="scss">
.login {
  padding: 24upx;
}
</style>
