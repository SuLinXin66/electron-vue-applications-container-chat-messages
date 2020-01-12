<template>
  <div class="user-info-head">
    <div class="left">
      <img src="../assets/timg.jpeg" alt="">
    </div>
    <div class="right">
      <div class="top">
        <span>无痕</span>
      </div>
      <div class="bottom">
        <span>哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈</span>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
  import {Component, Vue} from "vue-property-decorator";

  @Component
  export default class UserInfoHead extends Vue {

  }
</script>

<style lang="less" scoped>
  .user-info-head {
    position: relative;
    width: 100%;
    height: 100%;
    /*background-color: red;*/
    overflow: hidden;

    .left {
      width: 50px;
      height: 50px;
      float: left;
      position: relative;

      img {
        display: block;
        width: 100%;
        height: 100%;
        border-radius: 100%;
      }

      &::after {
        content: '';
        position: absolute;
        top: 0;
        right: 0;
        left: 0;
        bottom: 0;
        border-radius: 100%;
        background-color: rgba(0, 0, 0, 0.6);
      }
    }

    .right {
      position: absolute;
      left: 50px;
      right: 0;
      height: 50px;

      .top, .bottom {
        width: 100%;
        height: 60%;
        position: relative;

        span {
          display: block;
          width: 100%;
          overflow: hidden;
          text-overflow: ellipsis;
          white-space: nowrap;
          text-align: left;
        }

      }

      .top > span {
        font-size: 18px;
        position: absolute;
        bottom: 0;
        left: 3px;
        font-weight: bold;
      }

      .bottom > span {
        font-size: 10px;
        position: absolute;
        top: 0;
        left: 5px;
      }
    }
  }
</style>
