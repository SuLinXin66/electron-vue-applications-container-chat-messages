<template>
  <div id="app">
    <div class="left" v-if="messages.length > 1">
      <UserList></UserList>
    </div>
    <div :class="messages.length > 1 ? 'right active': 'right'">
      <button @click="test">点我</button>
      <button @click="test2">点我</button>
      <div class="user">
        <UserInfoHead/>
        <div class="btn-group">
          <i class="icon icon-zuixiaohua" title="最小化"></i>
          <i class="icon icon-fangda" title="最大化"></i>
          <i class="icon icon-close" title="关闭"></i>
        </div>
      </div>
      <div class="message">
        <UserMessage :now-user="nowUser" :to-user="messages[0]"/>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
  import {Component, Vue} from "vue-property-decorator";
  // import kscreenshot from "kscreenshot";
  import {UserInfo} from "@/types/user";
  import UserInfoHead from "@/components/UserInfoHead.vue"
  import UserMessage from "@/views/UserMessage.vue";
  import UserList from "@/views/UserList.vue";

  @Component({
    components: {
      UserList,
      UserInfoHead, UserMessage
    }
  })
  export default class App extends Vue {

    private nowUser!: UserInfo;

    private messages: Array<UserInfo> = [];

    private test2() {
      this.messages.splice(0, 1)
    }

    private test() {
      console.log(this.messages)
      console.log(this.messages.length)
      this.messages.push({
        id: 2,
        name: "slx",
        icon: ""
      })
      console.log(this.messages.length)
    }

    private created(): void {
      this.nowUser = {
        id: 1,
        name: 'wuhen',
        icon: 'haha'
      };

      this.messages.push({
        id: 2,
        name: 'wuhen2',
        icon: 'hehe'
      })
    }

    private mounted(): void {
      // console.log("dsfdfgsdfg")
      // new kscreenshot(65, function (base64) {
      //   return 'https://www.baidu.com/img/bd_logo1.png'
      // })
    }
  }
</script>

<style lang="less">
  #app {
    width: 100%;
    height: 100%;
    position: absolute;
    left: 0;
    bottom: 0;
    right: 0;
    top: 0;
    background-color: lightskyblue;

    > .right, > .left {
      position: absolute;
    }

    > .left {
      left: 0;
      width: 200px;
      top: 0;
      bottom: 0;
      background-color: #d9d9d9;
      border-right: 1px black;
    }

    > .right.active {
      left: 200px;
    }

    > .right {
      right: 0;
      bottom: 0;
      top: 0;
      left: 0;

      .user {
        position: relative;
        width: 100%;
        height: 80px;
        padding: 15px 50px 15px 15px;
        background-color: rgba(245, 245, 245, .7);

        & * {
          user-select: none;
        }

        .btn-group {
          width: 118px;
          position: absolute;
          top: 0;
          bottom: 0;
          right: 0;
          padding-top: 5px;

          i {
            position: relative;
            display: block;
            float: left;
            margin-left: 18px;
            cursor: default;

            &:hover {
              cursor: default;
              color: rgba(0, 0, 0, 0.3);
            }
          }

          /*  &::after {*/
          /*    content: "";*/
          /*    position: absolute;*/
          /*    left: 0;*/
          /*    top: 0;*/
          /*    bottom: 0;*/
          /*    right: 0;*/
          /*    background-color: red;*/
          /*  }*/
          /*}*/
        }
      }

      .message {
        position: absolute;
        top: 80px;
        bottom: 0;
        left: 0;
        right: 0;
        background-color: rgba(255, 255, 255, .8);
      }
    }

  }
</style>
