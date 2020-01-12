<template>
  <div id="app">
    <div class="user">
      <UserInfoHead/>
    </div>
    <div class="message">
      <UserMessage :now-user="nowUser" :to-user="messages[0]"/>
    </div>
  </div>
</template>

<script lang="ts">
  import {Component, Vue} from "vue-property-decorator";
  import {UserInfo} from "@/types/user";
  import UserInfoHead from "@/components/UserInfoHead.vue"
  import UserMessage from "@/views/UserMessage.vue";

  @Component({
    components: {
      UserInfoHead, UserMessage
    }
  })
  export default class App extends Vue {

    private nowUser!: UserInfo;

    private messages: Array<UserInfo> = [];

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

    .user {
      position: relative;
      width: 100%;
      height: 80px;
      padding: 15px 50px 15px 15px;
      background-color: rgba(245, 245, 245, .7);
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
</style>
