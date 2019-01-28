<template>
  <div class="container">
    <div class="recommend-header">
      <p>美食推荐</p>
    </div>

    <div class="shoppList" v-for="(item, index) in newShopp" :key="index">
      <div class="shoppListTitle">
        <div class="shoppListTitleIcon">店铺</div>
        {{item.name}}
      </div>
      <div class="shoppListDetail" v-for="(itemList, indexList) in item.shoppingList" :key="indexList">
        <div class="shoppListDetailImg">
          <img :src="itemList.shoppingImg" :alt="itemList.shoppingImgAlt">
        </div>
        <div class="shoppListDetailD">
          <p class="shoppListDetailDT">{{itemList.shoppListDetailDT}}</p>
          <p class="shoppListDetailDP">{{itemList.shoppListDetailDP}}</p>
          <p class="shoppListDetailDM">{{itemList.shoppListDetailDM}}</p>
        </div>
      </div>
    </div>

    <div class="loadMore">
      <i-load-more tip="暂无数据" :loading="loadingShow" />
    </div>

  </div>
</template>

<script>
let Fly = require('flyio/dist/npm/wx');
let fly = new Fly();

export default {
  data () {
    return {
      loadingShow: false,
      newShopp: []
    }
  },
  created () {
    this.getShopping();
  },
  methods: {
    getShopping () {
      fly.get("https://www.easy-mock.com/mock/5c45e5cbfb5b9a1c0746774e/example/shopping")
      .then( (res) => {
        if(res.status === 200) {
         let shopping = res.data;
          this.newShopp = shopping.data;
          this.loadingShow = true;
          console.log(this.newShopp );
        }
      })
      .catch((error) => {
        console.log(error);
      }) 
    }
  }
}
</script>

<style lang="less" scoped>
 .container{
   margin:0;
   padding: 0;
   background: #f4f4f4;
 }
 .recommend-header{
  width: 100%;
  height: 60rpx;
  background: #0097ff;
  p{
    color: #fff;
    padding-left: 20px;
  }
 }

 .shoppList{
    width: 700rpx;
    /*height: 400rpx;*/
    background: #fff;
    -webkit-border-radius: 20rpx;
    -moz-border-radius: 20rpx;
    border-radius: 20rpx;
    margin: 20rpx auto;
    padding: 0 0 20rpx 0;
    overflow: hidden;
    .shoppListTitle{
      width: 100%;
      height: 60rpx;
      line-height: 80rpx;
      color: #494949;
      font-size: 16px;
      margin-left: 30rpx;
      .shoppListTitleIcon{
        height: 40rpx;
        padding: 0 6rpx;
        background: #ffe142;
        float: left;
        font-size: 12px;
        color: #52250a;
        text-align: center;
        line-height: 40rpx;
        -webkit-border-radius: 3px;
        -moz-border-radius: 3px;
        border-radius: 3px;
        margin-right: 12rpx;
        margin-top: 20rpx;
      }
    }

    .shoppListDetail{
      width: 100%;
      height: 160rpx;
      margin: 20rpx 0;
      .shoppListDetailImg{
        width: 160rpx;
        height: 160rpx;
        overflow: hidden;
        float: left;
        margin-left: 30rpx;
        img{
          width: 100%;
          height: 100%;
        }
      }

    }
  }

.shoppListDetailD{
  float: left;
  width: 456rpx;
  height: 100%;
  margin-left: 30rpx;
  .shoppListDetailDT{
    overflow: hidden;
    -ms-text-overflow: ellipsis;
    text-overflow: ellipsis;
    white-space: nowrap;
    color: #333;
    font-size: 16px;
    font-weight: bold;
    line-height: 70rpx;
  }
  .shoppListDetailDP,
  .shoppListDetailDM{
    color: #717171;
    font-size: 14px;
    line-height: 40rpx;
  }
}

.loadMore{
  width: 100px;
}
</style>
