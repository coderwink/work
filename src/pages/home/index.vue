<template>
  <view>
    <view class="home_top">
      <image
        src="../../static/image/home/组 2（合并）（合并）.png"
        mode="widthFix"
      ></image>
    </view>
    <view class="home_search_wrap">
      <form>
        <input type="text" placeholder="输入搜索内容" />
        <text class="submit">搜索</text>
      </form>
    </view>
    <view class="home_main">
      <view v-for="(item, index) in title" :key="index" class=" home_main_item">
        <view @tap="viewClick(index)" :class="{ active: index === num }">{{
          item
        }}</view>
        <view :class="{ line: index === num }"></view>
      </view>
    </view>
    <view class="home_filter">
      <view v-for="(item, index) in condition"
            :key="index"
            class=" home_filter_item">
        <view @tap="filterClick(index)"
              :class="{ active2: index === num2 }"
              class="home_filter_mul">
          <text v-if="index==0">{{ name0 }}</text>
          <text v-if="index==1">{{ name1 }}</text>
          <text v-if="index==2">{{ name2 }}</text>
          <text v-if="index==3">{{ name3 }}</text>
          <text v-if="index==4">{{ name4 }}</text>
          <view class="home_filter_san">
            <image
              v-if="index === num2"
              src="../../static/image/home/多边形 1456.png"
            ></image>
            <image v-else src="../../static/image/home/多边形 1.png"></image>
          </view>
        </view>
      </view>
      <view class="popup_adds" v-show='isShow'>
        <view class="popup_top" v-if="checknum == 0">
          <view class="popup_top_left">
            <view class="popup_top_left_item" 
                  v-for='(item, index) in address' 
                  :key='index' 
                  @tap='addsClick(index)'
                  :class="{active3: num3 === index}"
                  >{{item}}</view>
          </view>
          <view class="popup_top_right" >
               <view v-for='(item, indey) in addressPort' 
                class="popup_top_right_wrap"
               :key='indey'              
               @tap='addsPortClick(indey)'
               >
               <view class="popup_top_right_item" :class="{active4: num4 === indey }" @tap="itemclick(checknum,0,indey)">
                 {{item}}0</view>
               </view> 
          </view>
        </view>
        <view class="popup_top" v-if="checknum == 1">
          <view class="popup_top_left">
            <view class="popup_top_left_item" 
                  v-for='(item, index) in address' 
                  :key='index' 
                  @tap='addsClick(index)'
                  :class="{active3: num3 === index}"
                  >{{item}}</view>
          </view>
          <view class="popup_top_right" >
               <view v-for='(item, indey) in addressPort' 
                class="popup_top_right_wrap"
               :key='indey'              
               @tap='addsPortClick(indey)'
               >
               <view class="popup_top_right_item" :class="{active4: num4 === indey }" >
                 {{item}}1</view>
               </view> 
          </view>
        </view>
        <view class="popup_top" v-if="checknum == 2">
          <view class="popup_top_left">
            <view class="popup_top_left_item" 
                  v-for='(item, index) in address' 
                  :key='index' 
                  @tap='addsClick(index)'
                  :class="{active3: num3 === index}"
                  >{{item}}</view>
          </view>
          <view class="popup_top_right" >
               <view v-for='(item, indey) in addressPort' 
                class="popup_top_right_wrap"
               :key='indey'              
               @tap='addsPortClick(indey)'
               >
               <view class="popup_top_right_item" :class="{active4: num4 === indey }" >
                 {{item}}2</view>
               </view> 
          </view>
        </view>
        <view class="popup_top" v-if="checknum == 3">
          <view class="popup_top_left">
            <view class="popup_top_left_item" 
                  v-for='(item, index) in address' 
                  :key='index' 
                  @tap='addsClick(index)'
                  :class="{active3: num3 === index}"
                  >{{item}}</view>
          </view>
          <view class="popup_top_right" >
               <view v-for='(item, indey) in addressPort' 
                class="popup_top_right_wrap"
               :key='indey'              
               @tap='addsPortClick(indey)'
               >
               <view class="popup_top_right_item" :class="{active4: num4 === indey }" >
                 {{item}}3</view>
               </view> 
          </view>
        </view>
        <view class="popup_top" v-if="checknum == 4">
          <view class="popup_top_left">
            <view class="popup_top_left_item" 
                  v-for='(item, index) in address' 
                  :key='index' 
                  @tap='addsClick(index)'
                  :class="{active3: num3 === index}"
                  >{{item}}</view>
          </view>
          <view class="popup_top_right" >
               <view v-for='(item, indey) in addressPort' 
                class="popup_top_right_wrap"
               :key='indey'              
               @tap='addsPortClick(indey)'
               >
               <view class="popup_top_right_item" :class="{active4: num4 === indey }" >
                 {{item}}4</view>
               </view> 
          </view>
        </view>
        <view class="popup_bottom">
          <view class='popup_bottom_item popup_bottom_left'>重置</view>
          <view class='popup_bottom_item popup_bottom_right'>确定</view>
        </view>
      </view>
    </view>
    <view class="home_main_content">
      <view
        v-for="(item, index) in message"
        :key="index"
        class="home_main_kuai"
      >
        <view class="home_main_wrap">
          <view style="width: 100%; height: 24rpx;"></view>
          <view class="home_main_content_top">
            <view class="post">{{ item.post }}</view>
            <view class="money">6k-10k</view>
          </view>
          <view class="home_main_content_center">
            <view class="needInfo_left">
              <view class="needInfo_left_item">{{ item.adds }}</view>
              <view class="needInfo_left_item">{{ item.edu }}</view>
              <view class="needInfo_left_item">{{ item.exp }}</view>
            </view>
            <view class="needInfo_right">三天前</view>
          </view>
          <view class="home_main_content_bottom">
            <view
              class="home_main_content_fuli"
              v-for="(item, indey) in item.fuli"
              :key="indey"
            >
              <view class="home_fuli_item">{{ item }}</view>
            </view>
            <view class="call"
              ><image src="../../static/image/home/电话 (1).png"></image
            ></view>
          </view>
          <view style="width: 100%; height: 23rpx;"></view>
        </view>
        <view
          style="width: 100%; height: 10rpx; background-color: #EEEEEE;"
        ></view>
      </view>
    </view>
  </view>
</template>
<script>
export default {
  data() {
    return {
      name0:"地址",
      name1:"职位",
      name2:"经验",
      name3:"待遇",
      name4:"学历",

      firstnum:0,//首次点击
      checknum:0,//默认选中
      num: 0,
      num2: 0,
      num3: 0,
      num4: 0,
      title: ["离我最近", "最新发布", "热门岗位"],
      condition: ["地址", "职位", "经验", "待遇", "学历"],
      message: [
        {
          post: "工程总监",
          adds: "南昌",
          edu: "本科",
          exp: "经验不限",
          fuli: ["五险一金", "节假路途", "五险一金"]
        },
        {
          post: "工程总监",
          adds: "南昌",
          edu: "本科",
          exp: "经验不限",
          fuli: ["五险一金", "节假路途", "五险一金"]
        },
        {
          post: "工程总监",
          adds: "南昌",
          edu: "本科",
          exp: "经验不限",
          fuli: ["五险一金", "节假路途", "五险一金"]
        },
        {
          post: "工程总监",
          adds: "南昌",
          edu: "本科",
          exp: "经验不限",
          fuli: ["五险一金", "节假路途", "五险一金"]
        },
        {
          post: "工程总监",
          adds: "南昌",
          edu: "本科",
          exp: "经验不限",
          fuli: ["五险一金", "节假路途", "五险一金"]
        },
        {
          post: "工程总监",
          adds: "南昌",
          edu: "本科",
          exp: "经验不限",
          fuli: ["五险一金", "节假路途", "五险一金"]
        },
        {
          post: "工程总监",
          adds: "南昌",
          edu: "本科",
          exp: "经验不限",
          fuli: ["五险一金", "节假路途", "五险一金"]
        },
        {
          post: "工程总监",
          adds: "南昌",
          edu: "本科",
          exp: "经验不限",
          fuli: ["五险一金", "节假路途", "五险一金"]
        }
      ],
      isShow: false,
      address: ["东湖区", "西湖区", "湾里湖区", "青山湖区", "新建区"],
      addressPort: ["广场0","广场1","广场2","广场3","广场4","八一广场","八一广场","八一广场","八一广场","八一广场","八一广场","八一广场","八一广场","八一广场","八一广场"]
    };
  },
  methods: {
    itemclick(res,index,indey){
      switch(index){
          case 0:
            this.name0=this.addressPort[indey]
            break;
          case 1:
            this.name1=this.addressPort[indey]
            break;
          case 2:
            this.name2=this.addressPort[indey]
            break;
          case 3:
            this.name3=this.addressPort[indey]
            break;
          case 4:
            this.name4=this.addressPort[indey]
            break;
      }
    },
    viewClick(index) {
      if (index != this.num) {
        this.num = index;
        console.log("----");
      }
    },
    filterClick(index) {
      if(this.firstnum == 0){
        this.isShow = true
        this.firstnum = 1
        this.num2 = index
        this.checknum = index
      }else{
        if(index != this.num2){
            this.num2 = index
            this.checknum = index
        }
      }



      /*
      if (index != this.num2) {
        this.num2 = index;
        console.log(index);
      }
      this.isShow = true
      //让盒子显示隐藏
      */
    },
    addsClick(index) {
      if(index != this.num3) {
        this.num3 = index;
      }
      console.log('-----');
      
    },
    addsPortClick(index) {
      if(index != this.num4) {
        this.num4 = index;
      }
    }

  }
};
</script>

<style lang='scss'>
.home_top {
  image {
    width: 749rpx;
    padding: 0;
    margin: 0;
  }
}
.home_search_wrap {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 30rpx 131rpx 13rpx 31rpx;
  form {
    input {
    }
    .submit {
    }
  }
  input {
    padding-left: 40rpx;
    font-size: 24rpx;
    width: 588rpx;
    height: 60rpx;
    background-color: #e1f2ff;
    border-radius: 30rpx;
  }
  .submit {
    position: absolute;
    right: 40rpx;
    top: 38rpx;
    font-size: 28rpx;
    color: #0084ee;
  }
}

.active {
  color: rgba(0, 132, 238, 1);
  font-size: 30rpx;
}
.active2 {
  color: #0084ee;
  font-size: 28rpx;
}
.active3 { 
  // background-color: #DCDCDC;
  // background-color: red;
  //  background-color: #DCDCDC;
  background-color: #fff !important;

}
.active4 {
  // background-color: #fff;
  border:2rpx solid rgba(0,132,238,1);
  color:#0084EE;
}
.home_main_content {
  .home_main_kuai {
    display: flex;
    flex-direction: column;
    align-items: center;
    .home_main_wrap {
      width: 690rpx;
      .home_main_content_top {
        display: flex;
        justify-content: space-between;
        align-items: center;
        height: 28rpx;
        .post {
          font-size: 30rpx;
          color: rgba(51, 51, 51, 1);
        }
        .money {
          font-size: 24rpx;
          color: #0084ee;
        }
      }
      .home_main_content_center {
        margin-top: 25rpx;
        display: flex;
        justify-content: space-between;
        align-items: center;
        font-size: 24rpx;
        height: 23rpx;
        color: rgba(181, 181, 181, 1);
        .needInfo_left {
          display: flex;
          justify-content: space-between;
          .needInfo_left_item::after {
            content: "|";
            padding: 0 24rpx;
            width: 1rpx;
            height: 16rpx;
          }
        }
        .needInfo_right {
          color: rgba(181, 181, 181, 1);
        }
      }
      .home_main_content_bottom {
        display: flex;
        justify-content: space-between;
        color: rgba(181, 181, 181, 1);
        // padding-top: 23rpx;
        .home_main_content_fuli {
          .home_fuli_item {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 142rpx;
            height: 38rpx;
            background: rgba(244, 244, 244, 1);
            border-radius: 5px;
            font-size: 24rpx;
            margin-top: 23rpx;
          }
        }
        .call {
          display: flex;
          justify-content: center;
          align-items: flex-end;
          image {
            width: 42rpx;
            height: 42rpx;
          }
        }
      }
    }
  }
}
.home_main {
  display: flex;
  margin-left: 10rpx;
  border-bottom: 2px solid #eeeeee;
  .home_main_item {
    width: 120rpx;
    font-size: 26rpx;
    color: rgba(51, 51, 51, 1);
    line-height: 34px;
    padding-left: 31rpx;
  }
  .line {
    width: 80rpx;
    height: 3rpx;
    background-color: #0084ee;
    margin-left: 21rpx;
    margin-top: -8rpx;
  }
}
.home_filter {
  display: flex;
  font-size: 28rpx;
  color: rgba(51, 51, 51, 1);
  line-height: 77rpx;
  border-bottom: 2px solid #eeeeee;
  position: relative;
  .home_filter_item {
    display: flex;
    justify-content: center;
    align-items: center;
    flex: 1;
    .home_filter_mul {
      display: flex;
      .home_filter_san {
      }
    }
    .home_filter_san {
      image {
        width: 18rpx;
        height: 15rpx;
        padding-left: 20rpx;
      }
    }
  }
}
.home_lowLoad {
  width: 100vh;
  height: 462rpx;
  position: absolute;
  background: rgba(0, 255, 255, 0.2);
  top: 0;
  right: 0;
}
.popup_adds {
  background-color: #fff;
  position: absolute;
  width: 100%;
  height: 550rpx;
  top: 80rpx;
  .popup_top {
    height: 463rpx;
    display: flex;
    .popup_top_left {
      width: 151rpx;
      display: flex;
      flex-direction: column;
       justify-content: center;
        align-items: center;
      .popup_top_left_item {
        justify-content: center;
        align-items: center;
        display: flex;
        height: 92rpx;
        width: 151rpx;
        background-color: #DCDCDC;
      }
    }
    .popup_top_right {
      padding-top: 24rpx;
      display: flex;
      flex-wrap: wrap;
      justify-content: space-evenly;
      align-items: flex-start;
      .popup_top_right_wrap {
          display: flex;
          justify-content: center;
          align-items: center;
          width:160rpx;
          height:60rpx;
        .popup_top_right_item {
          display: flex;
          justify-content: center;
          align-items: center;
          width:156rpx;
          height:56rpx;
          border-radius:5rpx;
          background-color:#F7F7F7;
      }
      }
      
    }
  }
  .popup_bottom {
    display: flex;
    .popup_bottom_item {
      flex: 1;
      display: flex;
      justify-content: center;
      align-items: center;
      font-size:28rpx;
      color:rgba(51,51,51,1);
      height: 83rpx;
    }
    .popup_bottom_left {

    }
    .popup_bottom_right {
      
    }
  }
}
</style>