<template>
  <div class="home">

    <van-nav-bar title="图书借阅" left-text="返回" right-text="按钮" left-arrow/>

    <van-swipe :autoplay="5000">
      <van-swipe-item v-for="(image, index) in images" :key="index">
        <img v-lazy="image">
      </van-swipe-item>
    </van-swipe>

  </div>
</template>

<script>
import Vue from "vue";
import { Lazyload } from "vant";
Vue.use(Lazyload);

import { bookList } from "@/api/book";

export default {
  data() {
    return {
      images: [
        "http://101.132.124.171:8000/1.jpg",
        "http://101.132.124.171:8000/2.jpg",
        "http://101.132.124.171:8000/3.jpg",
        "http://101.132.124.171:8000/4.jpg",
        "http://101.132.124.171:8000/4.jpg"
      ]
    };
  },
  mounted() {
    bookList()
      .then(response => {
        let aa = response.data;
        console.log(aa)
      })
      .catch(err => {
        console.log(err);
      });
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
  .aa {
    width: 100%;
    height: 260px;
  }
}
</style>