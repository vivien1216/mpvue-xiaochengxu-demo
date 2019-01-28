<template>
  <div class="container">
    <div class="user-info">
      <div class="image">
        <img src="/static/img/avatar.jpg" alt="" />
      </div>
      <div class="name">vivien</div>
    </div>

    <div class="main">
      <i-cell-group>
        <i-cell title="历史订单" is-link="true"  url="" link-type="switchTab">
            <i-icon slot="icon" type="document_fill" color="#0097ff" size="18" />
        </i-cell>
        <i-cell title="收货地址" is-link="true" url="">
          <i-icon slot="icon" type="coordinates_fill" color="#0097ff" size="18" />
        </i-cell>
        <i-cell title="联系我们" is-link="true" url="">
          <i-icon slot="icon" type="group_fill" color="#0097ff" size="18" />
        </i-cell>
        <i-cell title="联系商家" is-link="true" url="">
          <i-icon slot="icon" type="homepage_fill" color="#0097ff" size="18" />
        </i-cell>
        <i-cell title="意见反馈" is-link="true" url="">
          <i-icon slot="icon" type="like_fill" color="#0097ff" size="18" />
        </i-cell>
      </i-cell-group>
    </div>
    
    <div class="userLogIn">
      退出登陆
    </div>

  </div>
</template>

<script>

export default {
  
}
</script>

<style lang="less" scoped>
 .container{
   margin:0;
   padding: 0;
 }
 .user-info{
   width: 100%;
   height: 100px;
   background-color: #0097ff;
   color: #fff;
   .image{
     float: left;
     width: 50px;
     height: 50px;
     margin: 25px 15px;
     img{
       width: 100%;
       height: 100%;
       border-radius: 50%;
     }
   }  
   .name{
     height: 100px;
     line-height: 100px;
   } 
 }

 .main{
   width: 100%;
   background: #fff;
 }

.userLogIn{
  width: 100px;
  height: 40px;
  line-height: 40px;
  text-align: center;
  font-size: 16px;
  color: red;
  border: 1px solid #eee;
  border-radius: 3px;
  margin-top: 80px;
}
</style>
