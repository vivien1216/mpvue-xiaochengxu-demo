<template>
  <div class="container">

    <div class="headSearch">
        <input class="headSeachISearch" placeholder="请输入收货人姓名" />
    </div>

    <div class="banner">
      <img src="/static/img/banner.png" alt="banner">
    </div>

    <div class="menu">
      <div class="menuContent">
        <div class="menuContentList">
          <img src="/static/img/gssc.png" alt="gssc" />
        </div>
        <div class="menuContentList">
          <img src="/static/img/xlqg.png" alt="xlqg" />
        </div>
        <div class="menuContentList">
          <img src="/static/img/qbms.png" alt="qbms" />
        </div>
      </div>
    </div>

    <div class="main">
      <div class="sellers" v-for="(item,idx) in seller" :key="idx">
        <div class="header-info">
          <div class="image">
            <img :src="item.logo" alt="" />
          </div>
          <div class="info">
            <div class="seller-name">
              <span class="seller-block">店铺</span>
              <span class="name">{{item.title}}</span>
            </div>
            <div class="seller-count">{{item.sales}}</div>
            <div class="dispatch-money">{{item.distribution}}</div>
          </div>
        </div>
        <div class="sale">
          <div class="decrease">
            <img src="/static/img/decrease.png" alt="" />
            <span>{{item.less}}</span>
          </div>
          <div class="decrease">
            <img src="/static/img/discount.png" alt="" />
            <span>{{item.fold}}</span>
          </div>
        </div>
        <div class="shopping">
          <div class="shoppingContent" v-for="(itemShoop, itemIndex) in item.shopping" :key="itemIndex">
            <div class="shoppingContentImg">
              <img :src="itemShoop.shoopingImg" :alt="item.shoopimgAlt">
            </div>
            <p class="shoppingContentTitle">{{itemShoop.shoopingTitle}}</p>
            <p class="shoppingContentM"><span class="shoppingContentMA">{{itemShoop.shoopingMa}}￥</span><span class="shoppingContentMB">{{itemShoop.shoopingMb}}</span></p>
          </div>
        </div>
      </div>

      <div>
        <i-load-more tip="暂无数据" :loading="loadingShow" />
      </div>

    </div>

  </div>
</template>

<script>
let Fly = require('flyio/dist/npm/wx')
let fly = new Fly()

export default {
 data(){
   return {
    seller: [],
    loadingShow: false
   }
 },
 created () {
   this.getSellerData();
 },
 computed: {
   shopping () {
     const shopping = [];
     this.seller.forEach(item => {
      shopping.push(item);
     })
     return shopping
   }
 },
 methods: {
   getSellerData () {
     let _this = this
     fly.get("https://www.easy-mock.com/mock/5c45e5cbfb5b9a1c0746774e/example/foods")
        .then((res) => {
          if (res.status === 200) {
            let seller = res.data
            _this.loadingShow = false
            _this.seller = seller.data
          }
        })
        .catch(function (err) {
          _this.loadingShow = true
          console.log(err)
        })
   }
    
 }
}
</script>

<style lang="less" scoped>
/*search*/
 .headSearch{
   width: 100%;
   height: 60px;
   line-height: 50px;
   background-color: #0097ff;
   .headSeachISearch{
     width: 80%;
     height: 30px;
     line-height: 30px;
     font-size: 14px;
     margin: 10px auto;
     background-color: #fff;
     color: #000;
     border-radius: 10px;
     padding-left: 15px;
     padding-right: 15px;
   }
 }
 /*banner*/
 .banner{
    width: 100%;
    height: 320rpx;
    overflow: hidden;
    img{
      width: 100%;
      height: 100%;
    }
 }
 /*menu*/
  .menu{
    width: 100%;
    height: 280rpx;
    background: #fff;
    margin: 10rpx 0 20rpx 0;
    .menuContent {
      width: 690rpx;
      height: 216rpx;
      margin: 30rpx auto 0;
      .menuContentList{
        width: 216rpx;
        height: 216rpx;
        float: left;
        overflow: hidden;
      }
      .menuContentList:nth-child(2){
        margin: 0 21rpx;
      }

      .menuContentList img {
        width: 216rpx;
        height: 216rpx;
      }
    }
  }
  /*main*/
  .main{
    width: 100%;
    margin: auto;
    .sellers{
      width: 100%;
      height: 650rpx;
      margin: 10px auto;
      border-top: 1rpx solid #eee;
     -webkit-box-sizing: border-box;
     -moz-box-sizing: border-box;
     box-sizing: border-box;
     background: #fff;
     .header-info{
       width: 100%;
       height: 80px;
       margin: 10px;
       .image{
         float: left;
         width: 60px;
         height: 60px;
         margin: 10px;
         img{
           width: 100%;
           height: 100%;
         }
       }
       .info{
        float: left;
         font-size: 12px;
         padding-top: 5px;
         .seller-name{
           height: 30px;
           line-height: 30px;
           .seller-block{
             display: inline-block;
             width: 25px;
             height: 25px;
             text-align: center;
             line-height: 25px;
             color: #fff;
             background-color: orange;
             font-size: 10px;
             border-radius: 3px;
             margin-right: 15px;
           }
           .name{
             font-size: 18px;
           }
         }
       }
       .seller-count,.dispatch-money{
         color: #666;
         height: 15px;
         line-height:15px;
         margin-top: 5px;
       }
     }
     .sale{
       margin-left: 15px;
       .decrease{
         height: 25px;
         line-height: 25px;
         font-size: 13px;
         color: #666;
         img{
           display: inline-block;
           width: 20px;
           height: 20px;
           margin-right: 15px;
           vertical-align: middle;
         }
       }
     }

   .shopping{
    width: 100%;
    height: 340rpx;
    margin-top: 20rpx;
    margin-left: 15px;

    .shoppingContent{
      width: 216rpx;
      height: 340rpx;
      border: 1rpx solid #eee;
      float: left;
    }

    .shoppingContent:nth-child(2){
      margin: 0 15rpx;
    }
  }



  .shoppingContentImg{
    width: 216rpx;
    height: 216rpx;
    background: #a7a7a7;
    overflow: hidden;

    img {
      width: 100%;
      height: 100%;
    }
  }


  .shoppingContentTitle{
    color:#333;
    font-size:12px;
    margin:0 0 0 18rpx;
    padding:0;
    overflow: hidden;
    -ms-text-overflow: ellipsis;
    text-overflow: ellipsis;
    white-space: nowrap;
  }

  .shoppingContentM {
    margin: 0;
    padding: 0;
    .shoppingContentMA{
      color:#ff5339;
      font-size:18px;
      margin:0 0 0 18rpx;
    }
    .shoppingContentMB{
      color:#6b6b6b;
      font-size:12px;
      margin: 0;
      padding: 0;
      text-decoration: line-through;
    }
  }   
    }
  }
</style>