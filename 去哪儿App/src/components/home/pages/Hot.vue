<template>
  <div class="hots">
    <div class="hot-left iconfont">
      <div><img src="http://img1.qunarzz.com/piao/fusion/1711/16/bfbb9874e8f11402.png" alt=""></div>
      <span>本周热门榜单</span>
    </div>
    <div class="hot-right iconfont">
      <span>全部榜单</span>&#xe641;
    </div>
    <ul class="slideImg">
      <router-link to="/Details">
        <li v-for="item in hotlist">
          <div><img :src="item.imgUrl" alt=""></div>
          <p class="runout">{{item.touristSpot}}</p>
          <p><span>¥{{item.price}}</span>起</p>
          <div class="numberTitl" ><img :src="item.number" alt="" v-if="item.number"></div>
        </li>
      </router-link>
    </ul>
  </div>
</template>



<script>
  export default {
    props:["hotlist"]
  }
</script>



<style scoped>
  .hots{
    width: 100%;
    background-color: #fff;
    margin-top: 0.15rem;
  }
  .hots .hot-left{
    float: left;
    font-size: 0.16rem;
    color: #212121;
    padding:0.12rem 0.13rem;
    line-height: 0.22rem;
  }
  .hots .hot-left>div{
    width: 0.15rem;
    display: inline-block;
  }
  .hots .hot-left img{
    width: 100%;
    height: 100%;
  }
  .hots .slideImg{
    width: 100%;
    white-space: nowrap;
    overflow-x:scroll;
    overflow-y:hidden;
    padding:0 0.12rem;
    box-sizing: border-box;
  }
  .hots .hot-right{
  float: right;
  font-size: 0.12rem;
  color: #616161;
  padding:0.12rem 0.13rem;
  line-height: 0.22rem;
  }
  .hots .slideImg li{
  position: relative;
  display: inline-block;
  margin-right: 0.1rem;
  width: 1rem;
  height: 1rem;
  }
  .hots .slideImg li div:nth-child(1){
    width: 1rem;
    height: 1rem;
  }
  .hots .slideImg li img, .numberTitl img{
    width:100%;
    height: 100%;
  }
  .hots .slideImg li p{
    text-align: center;
    font-size: 0.12rem;
  }
  .hots .slideImg li p:nth-child(2){
    color: #212121;
    margin-top: 0.06rem;
    line-height: 0.16rem;
    text-overflow: ellipsis;
  }
  .hots .slideImg li p:nth-child(3){
    color: #616161;
  }
  .hots .slideImg li p:nth-child(3) span{
    color: #ff8300;
    line-height: 0.18rem;
  }
  .hots .numberTitl img{
    position: absolute;
    top: 0;
    left:0;
    width: 0.42rem!important;
    height: 0.20rem!important;
  }
</style>
