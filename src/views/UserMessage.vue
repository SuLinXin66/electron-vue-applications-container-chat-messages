<template>
  <div class="user-messages">
    <div class="bottom" style="height: 160px" ref="messageBottom">
      <div class="drop" @mousedown="mousedown($event)"></div>
      <div class="tools">
        <i class="iconfont icon-biaoqing" title="表情"></i>
        <i class="iconfont icon-14" title="图片"></i>
        <i class="iconfont icon-wenjian" title="文件"></i>
        <i class="iconfont icon-jietu" title="截图"></i>
        <div class="history">
          <i class="iconfont icon-lishijilu"></i>
          <span>聊天记录</span>
        </div>
      </div>
      <div @click="contentClick" class="content">
        <Scroll ref="contentScroll" :ops="ops">
          <div @click.stop="()=>{}" ref="textContent" contenteditable="true" id="text-content"></div>
        </Scroll>
      </div>
      <div class="btn-group">
        <Button @click="closeClick" style="font-size: 18px;">
          关闭
        </Button>
        <Dropdown trigger="click" style="margin-left: 20px">
          <ButtonGroup>
            <Button style="font-size: 18px;" @click.stop.prevent="sendMessage($event)" type="success">
              发&nbsp;&nbsp;&nbsp;&nbsp;送
            </Button>
            <Button type="success">
              <Icon type="ios-arrow-down"></Icon>
            </Button>
          </ButtonGroup>
          <DropdownMenu slot="list">
            <DropdownItem>驴打滚</DropdownItem>
            <DropdownItem>炸酱面</DropdownItem>
            <DropdownItem>豆汁儿</DropdownItem>
            <DropdownItem>冰糖葫芦</DropdownItem>
            <DropdownItem>北京烤鸭</DropdownItem>
          </DropdownMenu>
        </Dropdown>
      </div>

    </div>
  </div>
</template>

<script lang="ts">
  import {Component, Prop, Vue} from "vue-property-decorator";
  import {Dropdown, DropdownMenu, DropdownItem, Button, Icon, ButtonGroup} from "view-design"
  import Scroll from "vuescroll";

  import {UserInfo} from "@/types/user";

  import {Base64} from "js-base64";

  @Component({
    components: {
      Dropdown, DropdownMenu, DropdownItem, Button, Icon, ButtonGroup, Scroll
    }
  })
  export default class UserMessage extends Vue {

    @Prop({type: Object, required: true})
    private nowUser!: UserInfo;

    @Prop({type: Object, required: true})
    private toUser!: UserInfo;

    private ops = {
      bar: {
        background: '#888888'
      }
    }

    private messageHeight: number = 280;

    private sendMessage(e: any) {
      const text = (this.$refs["textContent"] as HTMLDivElement).innerText
      console.log(text);
      console.log(encodeURI(text));
      console.log(encodeURI(text).length);
      console.log(Base64.encode(text));
      console.log(Base64.encode(text).length);
    }

    private closeClick() {

      const content = `5aW955qE5ZWK8J+RjPCfkYwxMmFzZArlpb3nmoTllYrwn5GM8J+RjDEyYXNkCuWlveeahOWVivCfkYzwn5GMMTJhc2QK5aW955qE5ZWK8J+RjPCfkYwxMmFzZArlpb3nmoTllYrwn5GM8J+RjDEyYXNkCuWlveeahOWVivCfkYzwn5GMMTJhc2QK5aW955qE5ZWK8J+RjPCfkYwxMmFzZArlpb3nmoTllYrwn5GM8J+RjDEyYXNkCuWlveeahOWVivCfkYzwn5GMMTJhc2QK5aW955qE5ZWK8J+RjPCfkYwxMmFzZArlpb3nmoTllYrwn5GM8J+RjDEyYXNkCuWlveeahOWVivCfkYzwn5GMMTJhc2QK5aW955qE5ZWK8J+RjPCfkYwxMmFzZArlpb3nmoTllYrwn5GM8J+RjDEyYXNkCuWlveeahOWVivCfkYzwn5GMMTJhc2QK5aW955qE5ZWK8J+RjPCfkYwxMmFzZArlpb3nmoTllYrwn5GM8J+RjDEyYXNkCuWlveeahOWVivCfkYzwn5GMMTJhc2QK5aW955qE5ZWK8J+RjPCfkYwxMmFzZArlpb3nmoTllYrwn5GM8J+RjDEyYXNkCuWlveeahOWVivCfkYzwn5GMMTJhc2QK5aW955qE5ZWK8J+RjPCfkYwxMmFzZArlpb3nmoTllYrwn5GM8J+RjDEyYXNkCuWlveeahOWVivCfkYzwn5GMMTJhc2QK5aW955qE5ZWK8J+RjPCfkYwxMmFzZArlpb3nmoTllYrwn5GM8J+RjDEyYXNkCuWlveeahOWVivCfkYzwn5GMMTJhc2QK5aW955qE5ZWK8J+RjPCfkYwxMmFzZArlpb3nmoTllYrwn5GM8J+RjDEyYXNkCuWlveeahOWVivCfkYzwn5GMMTJhc2QK5aW955qE5ZWK8J+RjPCfkYwxMmFzZArlpb3nmoTllYrwn5GM8J+RjDEyYXNkCuWlveeahOWVivCfkYzwn5GMMTJhc2QK5aW955qE5ZWK8J+RjPCfkYwxMmFzZArlpb3nmoTllYrwn5GM8J+RjDEyYXNkCuWlveeahOWVivCfkYzwn5GMMTJhc2QK5aW955qE5ZWK8J+RjPCfkYwxMmFzZArlpb3nmoTllYrwn5GM8J+RjDEyYXNkCuWlveeahOWVivCfkYzwn5GMMTJhc2QK5aW955qE5ZWK8J+RjPCfkYwxMmFzZArlpb3nmoTllYrwn5GM8J+RjDEyYXNkCuWlveeahOWVivCfkYzwn5GMMTJhc2QK5aW955qE5ZWK8J+RjPCfkYwxMmFzZArlpb3nmoTllYrwn5GM8J+RjDEyYXNkCuWlveeahOWVivCfkYzwn5GMMTJhc2Q=`
      const urlContent = Base64.decode(content);
      (this.$refs["textContent"] as HTMLDivElement).innerText = urlContent
      this.contentClick();


    }

    private contentClick = () => {
      const ele = (this.$refs["textContent"] as HTMLDivElement);
      let range = document.createRange();
      range.selectNodeContents(ele);
      range.collapse(false);
      let sel = window.getSelection() as Selection;
      sel.removeAllRanges();
      sel.addRange(range);
      (this.$refs['contentScroll'] as any).scrollTo({
        x: '100%',
        y: '100%'
      })
    };

    private mousedown(e: any) {
      let formY = e.screenY;
      const messageBottom: HTMLDivElement = this.$refs["messageBottom"] as any;
      const height = parseInt(messageBottom.style.height as string);
      document.onmousemove = (e) => {
        const h = e.screenY - formY;
        const newHeight = height - h;
        messageBottom.style.height = newHeight + "px";
      };


      document.onmouseup = () => {
        document.onmousemove = null;
        document.onmouseup = null;
      }
    }

  }
</script>

<style lang="less" scoped>
  .user-messages {
    width: 100%;
    height: 100%;
    position: relative;

    .bottom {
      width: 100%;
      min-height: 160px;
      max-height: 80%;
      position: absolute;
      bottom: 0;
      left: 0;
      box-shadow: 0 0 6px #888888;


      .drop {
        position: absolute;
        left: 0;
        right: 0;
        top: 0;
        height: 2px;
        cursor: row-resize;
      }

      .tools {
        position: absolute;
        top: 2px;
        left: 0;
        right: 0;
        height: 32px;
        /*background-color: deepskyblue;*/

        * {
          user-select: none;
        }

        & > i {
          font-size: 28px;
          line-height: 32px;
          display: block;
          float: left;
          margin-left: 20px;
          cursor: pointer;
          vertical-align: middle;

          &:hover {
            color: rgba(0, 0, 0, 0.3);
          }

          &:nth-child(2) {
            margin-top: -2px;
          }

          &:nth-child(3) {
            font-size: 25px;
          }

          &:nth-child(4) {
            font-size: 30px;
            margin-top: 1px;
          }

          /*&:last-child{*/
          /*  font-size: 25px;*/
          /*  margin-top: 1px;*/
          /*}*/

        }

        .history {
          width: 108px;
          line-height: 32px;
          position: absolute;
          right: 0;
          top: 0;
          bottom: 0;
          /*background-color: deepskyblue;*/

          &:hover {
            color: rgba(0, 0, 0, 0.3);
            cursor: pointer;
          }

          & > i {
            font-size: 22px;
            margin-top: 1px;
          }

          & > span {
            font-size: 16px;
            display: inline-block;
            height: 100%;
            line-height: 32px;
            position: absolute;
            top: 0;
          }
        }
      }

      .content {
        position: absolute;
        top: 32px;
        bottom: 40px;
        left: 0;
        right: 0;
        overflow: hidden;
        cursor: text;
        /*background-color: skyblue;*/

        padding: 0 5px;

        #text-content {
          width: 100%;
          min-height: 100%;
          user-modify: read-write-plaintext-only;
          outline: 0;
        }
      }

      .btn-group {
        position: absolute;
        bottom: 8px;
        right: 12px;
      }
    }
  }
</style>
