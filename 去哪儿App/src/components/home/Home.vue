<template>
  <div class="box">
    <home-header></home-header>
    <Swiper :swiperlist="swiperlist"></Swiper>
    <Icon :iconlist="iconlist"></Icon>
    <Location></Location>
    <Hot :hotlist="hotlist"></Hot>
    <Like :likelist="likelist"></Like>
    <GoWhere :vacationList="vacationList"></GoWhere>
    <Footer></Footer>
  </div>
</template>


<script>
  import HomeHeader from './pages/HomeHeader'
  import Swiper from './pages/Swipper'
  import Icon from './pages/Icon'
  import Location from './pages/Location'
  import Hot from './pages/Hot'
  import Like from './pages/Like'
  import GoWhere from './pages/GoWhere'
  import Footer from './pages/Footer'
  import { mapState } from 'vuex'
  export default {
    data() {
      return {
        swiperlist: [],
        iconlist: [],
        hotlist: [],
        likelist: [],
        changeCity:"",
        vacationList:[],

      }
    },
    computed:{
      ...mapState(['city'])
    },
    components: {
      HomeHeader,
      Swiper,
      Icon,
      Location,
      Hot,
      Like,
      GoWhere,
      Footer
    },
    methods:{
      getHttp(){
        this.$http.get("http://39.106.168.20/php/home_data.php").then((res) => {
          let data = res.data.data;

          data.forEach((item,index)=>{
            if(item.city==this.city){
              this.swiperlist = item.swiperlist;
              this.iconlist = item.iconlist;
              this.hotlist = item.hotlist;
              this.likelist = item.likelist;
              this.vacationList = item.vacationList;
              console.log(this.hotlist)
            }
          })
       })
      }
    },
    mounted() {
      this.getHttp();
      this.changeCity=this.city;
    },
    activated(){
      if(this.changeCity!=this.city){
        this.getHttp();
        this.changeCity = this.city;
      }
    }
  }
</script>

<style>
  .box {
    background-color: #f5f5f5;
  }
</style>



