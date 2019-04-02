<template>
  <div  class="contain" @click="clickHandle">
    <swiper class="swiper" indicator-dots="true" autoplay="true" interval="5000" duration="1000">
      <block v-for="(item, index) in imageList" :index="index" :key="index">
        <swiper-item>
            <image :src="item.url" class="slide-image" mode="aspectFill" :style="{width: imageWidth + 'px'}" @click=""/>
        </swiper-item>
      </block>
    </swiper>

    <div class="guideList" >
        <div v-for="(item,index) in guideIcon" :index="index" :key="index" class="guide-item" @click="">
          <image :src= "item.url" class="guide-item-image"/>
          <span class="guide-item-text">{{item.text}}</span>
        </div>
    </div>

    <div class="searchList">
        <div v-for="(item,index) in searchList" :index="index" :key="index" class="search-item" @click="">
          <image :src="item.url" class="search-item-image"/>
          <span class="search-item-title">{{item.title}}</span>
          <span class="search-item-subtopic">{{item.subtopic}}</span>
        </div>
    </div>
    <div class="program-list">
      <span class="program-list-text">本地精选</span>
      <div v-for="(item,index) in programList" :index="index" :key="index" class="program-item" @click="">
        <image :src="item.imgurl" class="program-item-image"/>

        <div class="program-item-right">
          <span class="program-item-title">{{item.title}}</span>
          <span class="program-item-chargetype" v-if="item.type==='1'">
            免费
          </span>
          <span class="program-item-chargetype" v-else-if="item.type ==='2'">
            收费
          </span>

          <span class="program-item-institution">
            {{item.institution}}
          </span>
          <span class="program-item-institution">

          </span>
        </div>
      </div>

    </div>

    <!-- <div class="userinfo" @click="bindViewTap">
      <img class="userinfo-avatar" v-if="userInfo.avatarUrl" :src="userInfo.avatarUrl" background-size="cover" />
      <img class="userinfo-avatar" src="/static/images/user.png" background-size="cover" />

      <div class="userinfo-nickname">
        <card :text="userInfo.nickName"></card>
      </div>
    </div> -->
    <button @click="func_test">{{imageWidth}}</button>
    <!-- <div class="usermotto">
      <div class="user-motto">
        <card :text="motto"></card>
      </div>
    </div> -->

    <!-- <form class="form-container">
      <input type="text" class="form-control" :value="motto" placeholder="v-model" />
      <input type="text" class="form-control" v-model="motto" placeholder="v-model" />
      <input type="text" class="form-control" v-model.lazy="motto" placeholder="v-model.lazy" />
    </form> -->

    <!-- <a href="/pages/counter/main" class="counter">去往Vuex示例页面</a> -->

    <!-- <div class="all">
        <div class="left">
        </div>
        <div class="right">
        </div>
    </div> -->
  </div>
</template>

<script>
import card from '@/components/card'

export default {
  data () {
    return {
      motto: 'Hello miniprograme',
      imageWidth: mpvue.getSystemInfoSync().windowWidth,

      /*****************测试数据****************************************/
      imageList:[
        {url: '/static/images/1.jpg',link:''},
        {url: '/static/images/2.jpg',link:''},
        {url: '/static/images/3.jpg',link:''},
        {url: '/static/images/4.jpg',link:''},
        {url: '/static/images/5.jpg',link:''}
      ],
      guideIcon:[
        {url:'/static/images/address.png',link:'',text:"附近"},
        {url:'/static/images/address.png',link:'',text:"实验室"},
        {url:'/static/images/address.png',link:'',text:"今日推荐"},
        {url:'/static/images/address.png',link:'',text:"本周排行"}
      ],
      searchList:[
        {url:'',title:'找兴趣',link:"",subtopic:'发现天生的优势'},
        {url:'',title:'找机构',link:"",subtopic:'寻找合适的对的'},
        {url:'',title:'找工具',link:"",subtopic:'大家都在学什么'},
        {url:'',title:'试听课',link:"",subtopic:'免费免费免费'}
      ],
      programList:[
        //课程图片，  课程名，                课程ID,   课程截止日期，类型1.免费、2收费，地点，    机构名称             ，名额,    剩余名额
        {imgurl:'',title:"怡锦舞蹈试听课",programId:"",deadline:"",type:"1",location:"",institution:"怡锦舞蹈",quota:"",quotaLeft:""},
        {imgurl:'',title:"怡锦舞蹈试听课",programId:"",deadline:"",type:"1",location:"",institution:"怡锦舞蹈",quota:"",quotaLeft:""},
        {imgurl:'',title:"怡锦舞蹈试听课",programId:"",deadline:"",type:"2",location:"",institution:"怡锦舞蹈",quota:"",quotaLeft:""},
        {imgurl:'',title:"怡锦舞蹈试听课",programId:"",deadline:"",type:"1",location:"",institution:"怡锦舞蹈",quota:"",quotaLeft:""}
      ],
      /**************************测试数据********************************/
      userInfo: {
        nickName: 'mpvue',
        avatarUrl: 'http://mpvue.com/assets/logo.png'
      }
    }
  },

  components: {
    card
  },

  methods: {

    bindViewTap () {
      const url = '../logs/main'
      if (mpvuePlatform === 'wx') {
        mpvue.switchTab({ url })
      } else {
        mpvue.navigateTo({ url })
      }
    },
    clickHandle (ev) {
      console.log('clickHandle:', ev)
      // throw {message: 'custom test'}
    },
    func_test (){

      console.log(this.imageWidth);
    }
  },

  created () {
    // let app = getApp()
    // let imageLists = getImage();
  }
}
</script>

<style scoped>
body{
  width: 750rpx;
  overflow-x: hidden;
}
.program-item{
  /*width:100%;*/
  width: 750rpx;

  height: 200rpx;
  /*padding: 10rpx;*/
  background-color: #fff;
  /*border: 1px solid black;*/
}
.program-item-institution{
  display: block;
  font-size: 24rpx;
}
.program-item-image{
  display: inline-block;
  width:200rpx;
  height: 125rpx;
  position: relative;
  left:20rpx;
  top:25rpx;
  background-color: #dedede;
  /*border:1px solid black;*/
}
.program-item-chargetype{
  display: block;
  color:green;
  font-size:36rpx;
}
.program-item-right{
  position: relative;
  top:10rpx;
  left: 30rpx;
  display: inline-block;
  width: 480rpx;
  padding: 10rpx;
  height: 160rpx;
  /*border:1rpx solid red;*/
}
.program-item-title{
  font-size:30rpx;
}
.contain{
  background-color: #f2f4f5;
  width: 750rpx;
}
.userinfo {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.userinfo-avatar {
  width: 128rpx;
  height: 128rpx;
  margin: 20rpx;
  border-radius: 50%;
}

.userinfo-nickname {
  color: #aaa;
}

.usermotto {
  margin-top: 150px;
}

.form-control {
  display: block;
  padding: 0 12px;
  margin-bottom: 5px;
  /*border: 1px solid #ccc;*/
}
.all{
  width:7.5rem;
  height:1rem;
  background-color:blue;
}
.all:after{
  display:block;
  content:'';
  clear:both;
}
.left{
  float:left;
  width:3rem;
  height:1rem;
  background-color:red;
}

.right{
  float:left;
  width:4.5rem;
  height:1rem;
  background-color:green;
}

.guideList div{
  display: inline-block;
  width: 187.5rpx;
  height: 1.5rem;
  background-color: white;
}
.guide-item-image{
  display: block;
  width:40%;
  height: 50%;
  margin: 15rpx auto 0rpx auto;
}
.guide-item-text{
  display: inline-block;
  font-size: 14px;
  width:100%;
  text-align: center;
}
.searchList{
  margin-top: 20rpx;
}
.searchList div{
  background-color: white;
  display: inline-block;

  width:370rpx;
  height: 160rpx;
  margin-bottom: 10rpx;
}
.search-item:nth-child(even){
  float:right;
}
.search-item-image{
  position: relative;
  top:35rpx;
  left:50rpx;
  width:90rpx;
  height: 90rpx;
  border-radius: 45rpx;
  background-color: #dedede;
  /*border:1rpx solid black;*/
}
.search-item-title{
  font-size: 30rpx;
  position: relative;
  left: 70rpx;
  top:-20rpx;
}
.search-item-subtopic{
  position: relative;
  font-size: 24rpx;
  left: -20rpx;
  top:20rpx;
}
.program-list{
  padding-top: 20rpx;
  width: 750rpx;
  background-color: #fff;
}
.program-list-text{
  display: inline-block;
  width: 100%;
  text-align: center;
  font-size: 35rpx;
  margin-bottom: 25rpx;
}
</style>
