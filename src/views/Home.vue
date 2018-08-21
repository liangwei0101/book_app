<template>
  <div class="home">

    <van-nav-bar title="图书借阅" left-text="返回" right-text="按钮" left-arrow/>

    <van-pull-refresh v-model="isLoading" @refresh="onRefresh">
      <p>刷新次数: {{ count }}</p>
    </van-pull-refresh>

    <van-swipe style="height:200px" :autoplay="5000">
      <van-swipe-item v-for="(image, index) in images" :key="index">
        <img v-lazy="image">
      </van-swipe-item>
    </van-swipe>

    <van-cell-group>
      <van-cell value="|  新书上架" />
    </van-cell-group>
    <van-cell-group>
      <van-cell value="内容" icon="shop" is-link>
        <template slot="title">
          <span class="van-cell-text">单元格</span>
        </template>
      </van-cell>
      <van-cell title="单元格" icon="location" is-link />
    </van-cell-group>

  </div>
</template>

<script>
import Vue from "vue";
import { PullRefresh } from "vant";
import { Lazyload } from "vant";
Vue.use(Lazyload);
Vue.use(PullRefresh);

export default {
  data() {
    return {
      images: [
        "https://img.yzcdn.cn/public_files/2017/09/05/3bd347e44233a868c99cf0fe560232be.jpg",
        "https://img.yzcdn.cn/public_files/2017/09/05/c0dab461920687911536621b345a0bc9.jpg",
        "https://img.yzcdn.cn/public_files/2017/09/05/4e3ea0898b1c2c416eec8c11c5360833.jpg",
        "https://img.yzcdn.cn/public_files/2017/09/05/fd08f07665ed67d50e11b32a21ce0682.jpg"
      ],
       count: 0,
      isLoading: false
    };
  },
  mounted() {},
  methods: {
    onRefresh() {
      setTimeout(() => {
        this.$toast('刷新成功');
        this.isLoading = false;
        this.count++;
      }, 500);
    }
  }
};
</script>

<style lang="postcss">
.demo-lazyload {
  padding: 0 15px;
  img,
  div[lazy] {
    padding: 15px;
    width: 100%;
    height: 250px;
    margin: 10px 0 0;
    background-color: white;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.2);
    background-size: 315px 250px;
    background-position: 15px;
    background-repeat: no-repeat;
    box-sizing: border-box;
  }
  .van-doc-demo-block__title,
  .van-doc-demo-section__title {
    padding-left: 0;
  }
}
</style>