<template>
  <div class="user-list">
    <SearchItem></SearchItem>
    <div class="users">
      <Scroll :ops="ops">
        <UserItem></UserItem>
        <UserItem></UserItem>
        <UserItem></UserItem>
        <UserItem></UserItem>
        <UserItem></UserItem>
        <UserItem></UserItem>
        <UserItem></UserItem>
        <UserItem></UserItem>
        <UserItem></UserItem>
        <UserItem></UserItem>
        <UserItem></UserItem>
        <UserItem></UserItem>
        <UserItem></UserItem>
      </Scroll>
    </div>

  </div>
</template>

<script lang="ts">
  import {Component, Vue} from "vue-property-decorator";
  import SearchItem from "@/components/SearchItem.vue";
  import UserItem from "@/components/UserItem.vue";
  import Scroll from "vuescroll"


  @Component({
    components: {UserItem, SearchItem,Scroll}
  })
  export default class UserList extends Vue{
    private ops = {
      bar: {
        background: '#888888'
      }
    }
  }
</script>

<style lang="less" scoped>
  .user-list {
    padding: 5px 8px;
    width: 100%;
    height: 100%;
    position: relative;
    .users {
      width: 100%;
      /* height: 100%; */
      /* overflow: hidden; */
      position: absolute;
      bottom: 0;
      top: 50px;
      padding-right: 6px;
    }
  }
</style>
