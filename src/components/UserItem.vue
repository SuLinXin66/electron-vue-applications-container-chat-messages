<template>
  <div class="user-item">
    <img src="https://iknow-pic.cdn.bcebos.com/838ba61ea8d3fd1fe38494f03e4e251f94ca5f6e" alt="">
    <span>wuhen(苏林鑫)</span>
    <div class="close" title="关闭">x</div>
  </div>
</template>

<script lang="ts">
  import {Component, Vue} from "vue-property-decorator";

  @Component({components: {}})
  export default class UserItem extends Vue {

  }
</script>

<style lang="less" scoped>
  .user-item {
    width: 180px;
    margin-top: 10px;
    height: 50px;
    padding: 5px 0 5px 12px;
    position: relative;

    &, * {
      user-select: none;
    }

    &:hover {
      background-color: rgba(255, 255, 255, .3);
      cursor: pointer;
    }

    &:hover .close {
      display: block;
    }

    > .close {
      display: none;
      width: 16px;
      height: 16px;
      border-radius: 16px;
      background-color: #333333;
      position: absolute;
      right: 5px;
      top: 18px;
      font-size: 18px;
      text-align: center;
      line-height: 13px;
      color: #fff;
      font-weight: bold;

      &:hover {
        background-color: #c00;
      }
    }

    > img {
      display: inline-block;
      width: 40px;
      height: 40px;
      border-radius: 100%;
    }

    > span {
      position: absolute;
      display: inline-block;
      right: 0;
      left: 58px;
      top: 0;
      bottom: 0;
      text-align: left;
      font-size: 14px;
      color: black;
      line-height: 50px;
      overflow: hidden;
      text-overflow: ellipsis;
      white-space: nowrap;
    }
  }
</style>
