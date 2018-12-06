<template>
  <div class="container" @click="clickHandle('test click', $event)">

    <div class="banner"></div>

    <section>
      <p class="title">热门游戏</p>
      <ul>
        <li v-for="n in 8">
          <img src="" alt="" @click="jump()">
          <p class="game-title">拇指射箭</p>
          <p class="play-count">888万人玩</p>
        </li>
      </ul>
    </section>
    <section>
      <p class="title">经典推荐</p>
      <ul>
        <li v-for="n in 8">
          <img src="" alt="" @click="jump()">
          <p class="game-title">拇指射箭</p>
          <p class="play-count">888万人玩</p>
        </li>
      </ul>
    </section>
    <section>
      <p class="title">扫码1区</p>
      <ul>
        <li v-for="n in 8">
          <img src="" alt="" @click="jump()">
          <p class="game-title">拇指射箭</p>
          <p class="play-count">888万人玩</p>
        </li>
      </ul>
    </section>
    <section>
      <p class="title">扫码2区</p>
      <ul>
        <li v-for="n in 8">
          <img src="" alt="" @click="jump()">
          <p class="game-title">拇指射箭</p>
          <p class="play-count">888万人玩</p>
        </li>
      </ul>
    </section>
    <section>
      <p class="title">扫码3区</p>
      <ul>
        <li v-for="n in 8">
          <img src="" alt="" @click="jump()">
          <p class="game-title">拇指射箭</p>
          <p class="play-count">888万人玩</p>
        </li>
      </ul>
    </section>

    <!-- <div class="userinfo" @click="bindViewTap">
      <img class="userinfo-avatar" v-if="userInfo.avatarUrl" :src="userInfo.avatarUrl" background-size="cover" />
      <div class="userinfo-nickname">
        <card :text="userInfo.nickName"></card>
      </div>
    </div>

    <div class="usermotto">
      <div class="user-motto">
        <card :text="motto"></card>
      </div>
    </div>

    <form class="form-container">
      <input type="text" class="form-control" v-model="motto" placeholder="v-model" />
      <input type="text" class="form-control" v-model.lazy="motto" placeholder="v-model.lazy" />
    </form>
    <a href="/pages/counter/main" class="counter">去往Vuex示例页面</a> -->
  </div>
</template>

<script>
import card from '@/components/card'

export default {
  data () {
    return {
      motto: 'Hello World',
      userInfo: {}
    }
  },

  components: {
    card
  },

  methods: {
    jump() {
      wx.navigateToMiniProgram({
        appId: 'xxxxxxxxxxxxxxxxxx', // 要跳转的小程序的appid
        path: 'page/index/index', // 跳转的目标页面
        extarData: {
          open: 'auth'
        },
        success(res) {
          // 打开成功  
        }
    }) 
    },
    bindViewTap () {
      const url = '../logs/main'
      wx.navigateTo({ url })
    },
    getUserInfo () {
      // 调用登录接口
      wx.login({
        success: () => {
          wx.getUserInfo({
            success: (res) => {
              this.userInfo = res.userInfo
            }
          })
        }
      })
    },
    clickHandle (msg, ev) {
      console.log('clickHandle:', msg, ev)
    }
  },

  created () {
    // 调用应用实例的方法获取全局数据
    this.getUserInfo()
  }
}
</script>

<style scoped lang="scss">
.banner {
  width: 100%;
  height: 200px;
  background-color: green;
}
section {
  width: calc(100% - 10px);
  margin-top: 10px;
  padding: 10px 0;
  background-color: #fff;
  border-radius: 8px;
  .title {
    padding-left: 5px;
    margin-left: 15px;
    border-left: 3px solid orange;
  }
  ul {
    margin: 0 auto;
    margin-top: 20px;
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
    list-style: none;
    border-radius: 8px;
    li {
      margin-left: 15px;
      margin-right: 15px;
      margin-bottom: 15px;
      img {
        margin: 0 auto;
        display: block;
        width: 60px;
        height: 60px;
        background-color: red;
        border-radius: 8px;
      }
      .game-title {
        font-size: 14px;
        text-align: center;
        font-weight: bold;
      }
      .play-count {
        font-size: 12px;
        text-align: center;
        color: #ccc;
      }
    }
    // li:nth-child(4n) {
    //   margin-right: 0;
    // }
  }
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
  border: 1px solid #ccc;
}

.counter {
  display: inline-block;
  margin: 10px auto;
  padding: 5px 10px;
  color: blue;
  border: 1px solid blue;
}
</style>
