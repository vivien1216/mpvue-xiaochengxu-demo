<template>
  <div class="container">
    <div class="orderNoList">
      <div class="orderImg">
          <img src="/static/img/order.png" alt="ndd">
        </div>
        <p class="orderTitle">当前没有订单哦！</p>
      </div>
  </div>
</template>

<script>

export default {

}
</script>

<style lang="less" scoped>
.container{
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  margin: 0;
  padding: 0;
  background: #f4f4f4;
}
.orderImg {
    width: 130rpx;
    height: 120rpx;
    margin: 460rpx auto 0;
    img{
      width: 100%;
      height: 100%;
    }
  }

.orderTitle{
  text-align: center;
  font-size: 16px;
  color: #aaaaaa;
  margin-top: 40rpx;
}
</style>
