<template>
  <div class="flex content-around box">
    <div @click="onClick_1" :data-url="item.url" :key="item.index" v-for="(item, index) in data">
      <div class="flex bd">
        <image
          class="layer"
          src="https://img.alicdn.com/tfs/TB1bLoWoYH1gK0jSZFwXXc7aXXa-684-684.png"
          mode="aspectFill"
        />
        <image class="bg" :src="item.coverImage" mode="aspectFill" />
        <div class="flex item-center wrap">
          <image
            class="riverdinwei"
            src="https://img.alicdn.com/tfs/TB1mtZRoVT7gK0jSZFpXXaTkpXa-28-36.png"
            mode="aspectFill"
          />
          <text class="distance">距离500m</text>
        </div>
      </div>
      <div class="flex content-center main">
        <text class="title">{{ item.title }}</text>
      </div>
      <div class="flex item-center content-between ft">
        <div class="flex item-center block">
          <image
            class="xianjin"
            src="https://img.alicdn.com/tfs/TB1OvsYoW61gK0jSZFlXXXDKFXa-60-60.png"
            mode="aspectFill"
          />
          <text class="fashionHome">{{ item.user.userName }}</text>
        </div>
        <div v-if="isReadCountShow(item.readCount)" class="flex item-center group">
          <image
            class="favorite"
            src="https://img.alicdn.com/tfs/TB1arwYo7T2gK0jSZFkXXcIQFXa-46-44.png"
            mode="aspectFill"
          />
          <text class="num">{{ item.readCount }}</text>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { Component, Vue } from 'vue-property-decorator';

@Component
export default class Page extends Vue {
  data = [
    {
      title: '小户型卫浴怎样才能装得高大上？',
      coverImage: 'https://img.alicdn.com/tfs/TB1Txq6o7T2gK0jSZFkXXcIQFXa-684-684.png',
      readCount: 200,
      user: { userImage: 'https://img.alicdn.com/tfs/TB1DWe6oYj1gK0jSZFOXXc7GpXa-60-60.png', userName: '时尚家居' },
      url: 'https://www.imgcook.com'
    },
    {
      title: '拥有超多功能的40平米简约小公寓了解一下',
      coverImage: 'https://img.alicdn.com/tfs/TB1XRQTo7P2gK0jSZPxXXacQpXa-684-648.png',
      readCount: 500,
      user: { userImage: 'https://img.alicdn.com/tfs/TB1DWe6oYj1gK0jSZFOXXc7GpXa-60-60.png', userName: '花花设计工作' },
      url: 'https://www.imgcook.com/docs'
    }
  ];
  created() {
    console.log('super props');
    this.fetch_example();
    this.jsonp_example();
  }
  updated() {}
  isReadCountShow(readCount) {
    return readCount > 300;
  }
  fetch_example() {
    fetch('https://jsonplaceholder.typicode.com/todos/1', { method: 'GET', headers: '{"Content-Type":"json"}' })
      .then(response => response.json())
      .then((data, error) => {
        console.log('fetch example: ', data, error);
        return data;
      })
      .catch(e => {
        console.log('error', e);
      });
  }
  jsonp_example() {
    jsonp('https://assets.airbnb.com/frontend/search_results.js', { jsonpCallbackFunction: 'search_results', body: {} })
      .then(response => response.json())
      .then((data, error) => {
        console.log('jsonp example: ', data, error);
        return data;
      })
      .catch(e => {
        console.log('error', e);
      });
  }
  onClick_1(e) {
    window.open(this.item.url, '_blank');
  }
}
</script>
<style lang="scss">
.box {
  height: 534px;
  .bd {
    position: relative;
    opacity: 1;
    width: 342px;
    height: 342px;
    .layer {
      position: absolute;
      top: 0;
      left: 0;
      width: 342px;
      height: 342px;
      overflow: hidden;
    }
    .bg {
      position: absolute;
      top: 0;
      left: 0;
      opacity: 1;
      width: 342px;
      height: 342px;
    }
    .wrap {
      box-sizing: border-box;
      position: relative;
      margin-top: 18px;
      margin-left: 18px;
      border-radius: 15px;
      background-color: rgba(0, 0, 0, 0.4);
      padding-right: 9px;
      padding-left: 10px;
      height: 30px;
      .riverdinwei {
        opacity: 1;
        width: 14px;
        height: 18px;
      }
      .distance {
        margin-left: 4px;
        height: 22px;
        font-size: 18px;
        color: #ffffff;
        line-height: 22px;
        white-space: nowrap;
      }
    }
  }
  .main {
    background-color: #ffffff;
    width: 342px;
    height: 114px;
    .title {
      margin-top: 22px;
      width: 300px;
      height: 88px;
      font-size: 30px;
      line-height: 44px;
      overflow: hidden;
      text-overflow: ellipsis;
    }
  }
  .ft {
    box-sizing: border-box;
    border-bottom-left-radius: 12px;
    border-bottom-right-radius: 12px;
    background-color: #ffffff;
    padding-right: 17px;
    padding-left: 18px;
    width: 342px;
    height: 78px;
    overflow: hidden;
    .block {
      height: 30px;
      .xianjin {
        width: 30px;
        height: 30px;
      }
      .fashionHome {
        margin-left: 6px;
        height: 28px;
        font-weight: 300;
        font-size: 24px;
        color: #666666;
        line-height: 28px;
        white-space: nowrap;
      }
    }
    .group {
      height: 30px;
      .favorite {
        width: 22px;
        height: 22px;
      }
      .num {
        margin-left: 5px;
        height: 26px;
        font-size: 22px;
        color: #999999;
        line-height: 26px;
        white-space: nowrap;
      }
    }
  }
}
</style>
