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

      // let filePath = 'http://qiniu.jnwtv.com/LC20180417174434604455636.jpg';
      //filePath为后台返回的图片地址
      // (this.$refs["textContent"] as HTMLDivElement).focus();
      // document.execCommand('InsertImage', false, filePath);
      const content = `8J+YgPCfmIHwn5iC8J+Yg/CfmITwn5iF8J+YhvCfmInwn5iK8J+Yi/CfmI7wn5iN8J+YmPCfmJfwn5iZ8J+YmuKYuvCfmIfwn5iQ8J+YkfCfmLbwn5iP8J+Yo/CfmKXwn5iu8J+Yr/CfmKrwn5ir8J+YtPCfmIzwn5ib8J+YnPCfmJ3wn5iS8J+Yk/CfmJTwn5iV8J+YsvCfmLfwn5iW8J+YnvCfmJ/wn5ik8J+YovCfmK3wn5im8J+Yp/CfmKjwn5is8J+YsPCfmLHwn5iz8J+YtfCfmKHwn5igCmVtb2pp5Lq654mpKOmdnuWbvueJh+WPr+WkjeWItikK4oaR6L+U5Zue6aG26YOoCgrwn5Gm8J+Rp/Cfkajwn5Gp8J+RtPCfkbXwn5G28J+RsfCfka7wn5Gy8J+Rs/Cfkbfwn5G48J+SgvCfjoXwn5Gw8J+RvPCfkobwn5KH8J+ZjfCfmY7wn5mF8J+ZhvCfkoHwn5mL8J+Zh/CfmYzwn5mP8J+RpPCfkaXwn5q28J+Pg/Cfka/wn5KD8J+Rq/Cfkazwn5Gt8J+Sj/CfkpHwn5GqCmVtb2pp5omL5Yq/KOmdnuWbvueJh+WPr+WkjeWItikK4oaR6L+U5Zue6aG26YOoCgrwn5Kq8J+RiPCfkYnimJ3wn5GG8J+Rh+KcjOKci/CfkYzwn5GN8J+RjuKcivCfkYrwn5GL8J+Rj/CfkZDinI0KZW1vamnml6XluLgo6Z2e5Zu+54mH5Y+v5aSN5Yi2KQrihpHov5Tlm57pobbpg6gKCvCfkaPwn5GA8J+RgvCfkYPwn5GF8J+RhPCfkovwn5GT8J+RlPCfkZXwn5GW8J+Rl/CfkZjwn5GZ8J+RmvCfkZvwn5Gc8J+RnfCfjpLwn5K88J+RnvCfkZ/wn5Gg8J+RofCfkaLwn5GR8J+RkvCfjqnwn46T8J+ShPCfkoXwn5KN8J+MggplbW9qaeaJi+acuijpnZ7lm77niYflj6/lpI3liLYpCuKGkei/lOWbnumhtumDqAoK8J+TsfCfk7Lwn5O28J+Ts/Cfk7TimI7wn5Oe8J+Tn/Cfk6AKZW1vamnlhazlhbEo6Z2e5Zu+54mH5Y+v5aSN5Yi2KQrihpHov5Tlm57pobbpg6gKCuKZu/Cfj6fwn5qu8J+asOKZv/Cfmrnwn5q68J+au/Cfmrzwn5q+4pqg8J+auOKblPCfmqvwn5qz8J+arfCfmq/wn5qx8J+at/CflJ7wn5KICmVtb2pp5Yqo54mpKOmdnuWbvueJh+WPr+WkjeWItikK4oaR6L+U5Zue6aG26YOoCgrwn5mI8J+ZifCfmYrwn5C18J+QkvCfkLbwn5CV8J+QqfCfkLrwn5Cx8J+YuvCfmLjwn5i58J+Yu/CfmLzwn5i98J+ZgPCfmL/wn5i+8J+QiPCfkK/wn5CF8J+QhvCfkLTwn5CO8J+QrvCfkILwn5CD8J+QhPCfkLfwn5CW8J+Ql/CfkL3wn5CP8J+QkfCfkJDwn5Cq8J+Qq/CfkJjwn5Ct8J+QgfCfkIDwn5C58J+QsPCfkIfwn5C78J+QqPCfkLzwn5C+8J+QlPCfkJPwn5Cj8J+QpPCfkKXwn5Cm8J+Qp/CfkLjwn5CK8J+QovCfkI3wn5Cy8J+QifCfkLPwn5CL8J+QrPCfkJ/wn5Cg8J+QofCfkJnwn5Ca8J+QjPCfkJvwn5Cc8J+QnfCfkJ7wn6aLCmVtb2pp5qSN54mpKOmdnuWbvueJh+WPr+WkjeWItikK4oaR6L+U5Zue6aG26YOoCgrwn5KQ8J+MuPCfkq7wn4y58J+MuvCfjLvwn4y88J+Mt/CfjLHwn4yy8J+Ms/CfjLTwn4y18J+MvvCfjL/wn42A8J+NgfCfjYLwn42DCmVtb2pp6Ieq54S2KOmdnuWbvueJh+WPr+WkjeWItikK4oaR6L+U5Zue6aG26YOoCgrwn4yN8J+MjvCfjI/wn4yQ8J+MkfCfjJLwn4yT8J+MlPCfjJXwn4yW8J+Ml/CfjJjwn4yZ8J+MmvCfjJvwn4yc4piA8J+MnfCfjJ7irZDwn4yf8J+MoOKYgeKbheKYlOKaoeKdhPCflKXwn5Kn8J+MigplbW9qaemlrumjnyjpnZ7lm77niYflj6/lpI3liLYpCuKGkei/lOWbnumhtumDqAoK8J+Nh/CfjYjwn42J8J+NivCfjYvwn42M8J+NjfCfjY7wn42P8J+NkPCfjZHwn42S8J+Nk/CfjYXwn42G8J+MvfCfjYTwn4yw8J+NnvCfjZbwn42X8J+NlPCfjZ/wn42V8J+Ns/CfjbLwn42x8J+NmPCfjZnwn42a8J+Nm/CfjZzwn42d8J+NoPCfjaLwn42j8J+NpPCfjaXwn42h8J+NpvCfjafwn42o8J+NqfCfjarwn46C8J+NsPCfjavwn42s8J+NrfCfja7wn42v8J+NvOKYlfCfjbXwn4228J+Nt/Cfjbjwn4258J+NuvCfjbvwn420CmVtb2pp5paH5L2TKOmdnuWbvueJh+WPr+WkjeWItikK4oaR6L+U5Zue6aG26YOoCgrwn46q8J+OrfCfjqjwn46w8J+ao/Cfm4Dwn46r8J+PhuKaveKavvCfj4Dwn4+I8J+PifCfjr7wn46x8J+Os+Kbs/CfjqPwn4698J+Ov/Cfj4Lwn4+E8J+Ph/Cfj4rwn5q08J+atfCfjq/wn46u8J+OsvCfjrfwn4648J+OuvCfjrvwn46sCmVtb2pp5oGQ5oCWKOmdnuWbvueJh+WPr+WkjeWItikK4oaR6L+U5Zue6aG26YOoCgrwn5iI8J+Rv/Cfkbnwn5G68J+SgOKYoPCfkbvwn5G98J+RvvCfkqMKZW1vamnml4XmuLgo6Z2e5Zu+54mH5Y+v5aSN5Yi2KQrihpHov5Tlm57pobbpg6gKCvCfjIvwn5e78J+PoPCfj6Hwn4+i8J+Po/Cfj6Twn4+l8J+PpvCfj6jwn4+p8J+PqvCfj6vwn4+s8J+PrfCfj6/wn4+w8J+SkvCfl7zwn5e94puq4puy8J+MgfCfjIPwn4yG8J+Mh/CfjInwn4yM8J+OoPCfjqHwn46i8J+agvCfmoPwn5qE8J+ahfCfmobwn5qH8J+aiPCfmonwn5qK8J+anfCfmp7wn5qL8J+ajPCfmo3wn5qO8J+aj/CfmpDwn5qR8J+akvCfmpPwn5qU8J+alfCfmpbwn5qX8J+amPCfmprwn5qb8J+anPCfmrLim73wn5qo8J+apfCfmqbwn5qn4pqT4pu18J+apPCfmqLinIjwn5K68J+agfCfmp/wn5qg8J+aofCfmoDwn46R8J+Xv/Cfm4Lwn5uD8J+bhPCfm4UKZW1vamnnianlk4Eo6Z2e5Zu+54mH5Y+v5aSN5Yi2KQrihpHov5Tlm57pobbpg6gKCvCfkozwn5KO8J+UqvCfkojwn5qq8J+avfCfmr/wn5uB4oyb4o+z4oya4o+w8J+OiPCfjonwn46K8J+OjvCfjo/wn46Q8J+OgPCfjoHwn5Ov8J+Tu/Cfk7Hwn5Oy4piO8J+TnvCfk5/wn5Og8J+Ui/CflIzwn5K78J+SvfCfkr7wn5K/8J+TgPCfjqXwn5O68J+Tt/Cfk7nwn5O88J+UjfCflI7wn5Ss8J+UrfCfk6Hwn5Kh8J+UpvCfj67wn5OU8J+TlfCfk5bwn5OX8J+TmPCfk5nwn5Oa8J+Tk/Cfk4Pwn5Oc8J+ThPCfk7Dwn5OR8J+UlvCfkrDwn5K08J+StfCfkrbwn5K38J+SuPCfkrPinInwn5On8J+TqPCfk6nwn5Ok8J+TpfCfk6bwn5Or8J+TqvCfk6zwn5Ot8J+TruKcj+KckvCfk53wn5OB8J+TgvCfk4Xwn5OG8J+Th/Cfk4jwn5OJ8J+TivCfk4vwn5OM8J+TjfCfk47wn5OP8J+TkOKcgvCflJLwn5ST8J+Uj/CflJDwn5SR8J+UqPCflKvwn5Sn8J+UqfCflJfwn5KJ8J+SivCfmqzwn5Su8J+aqfCfjozwn5Km8J+SqAplbW9qaeagh+W/lyjpnZ7lm77niYflj6/lpI3liLYpCuKGkei/lOWbnumhtumDqAoK4pmg4pml4pmm4pmj8J+AhPCfjrTwn5SH8J+UiPCflInwn5SK8J+TovCfk6Pwn5Kk8J+SovCfkqzwn5Kt4pmo8J+MgPCflJTwn5SV4pyh4pyd8J+Ur/Cfk5vwn5Sw8J+UseKtleKcheKYkeKclOKcluKdjOKdjuKeleKeluKel+KesOKev+OAveKcs+KctOKdh+KAvOKBieKdk+KdlOKdleKdl8Kpwq7ihKLwn46m8J+UhfCflIbwn5Kv8J+UoPCflKHwn5Si8J+Uo/CflKTwn4Ww8J+GjvCfhbHwn4aR8J+GkvCfhpPihLnwn4aU4pOC8J+GlfCfhpbwn4W+8J+Gl/Cfhb/wn4aY8J+GmfCfhprwn4iB8J+IgvCfiLfwn4i28J+Ir/CfiZDwn4i58J+ImvCfiLLwn4mR8J+IuPCfiLTwn4iz44qX44qZ8J+IuvCfiLXilqrilqvil7vil7zil73il77irJvirJzwn5S28J+Ut/CflLjwn5S58J+UuvCflLvwn5Kg8J+UsvCflLPimqrimqvwn5S08J+UtQplbW9qaeeUn+iClijpnZ7lm77niYflj6/lpI3liLYpCuKGkei/lOWbnumhtumDqAoK8J+QgfCfkILwn5CF8J+Qh/CfkInwn5CN8J+QjvCfkJDwn5CS8J+Qk/CfkJXwn5CWCmVtb2pp5pif5bqnKOmdnuWbvueJh+WPr+WkjeWItikK4oaR6L+U5Zue6aG26YOoCgrimYjimYnimYrimYvimYzimY3imY7imY/imZDimZHimZLimZPim44KZW1vamnpkp/ooago6Z2e5Zu+54mH5Y+v5aSN5Yi2KQrihpHov5Tlm57pobbpg6gKCvCflZvwn5Wn8J+VkPCflZzwn5WR8J+VnfCflZLwn5We8J+Vk/CflZ/wn5WU8J+VoPCflZXwn5Wh8J+VlvCflaLwn5WX8J+Vo/CflZjwn5Wk8J+VmfCflaXwn5Wa8J+VpuKMm+KPs+KMmuKPsOKPseKPsvCflbAKZW1vamnlv4PlvaIo6Z2e5Zu+54mH5Y+v5aSN5Yi2KQrihpHov5Tlm57pobbpg6gKCvCfkpjinaTwn5KT8J+SlPCfkpXwn5KW8J+Sl/Cfkpnwn5Ka8J+Sm/Cfkpzwn5Kd8J+SnvCfkp/inaMKZW1vamnoirHojYko6Z2e5Zu+54mH5Y+v5aSN5Yi2KQrihpHov5Tlm57pobbpg6gKCvCfkpDwn4y48J+SrvCfjLnwn4y68J+Mu/CfjLzwn4y38J+MsfCfjL/wn42ACmVtb2pp5qCR5Y+2KOmdnuWbvueJh+WPr+WkjeWItikK4oaR6L+U5Zue6aG26YOoCgrwn4y/8J+NgPCfjYHwn42C8J+NgwplbW9qaeaciOS6rijpnZ7lm77niYflj6/lpI3liLYpCuKGkei/lOWbnumhtumDqAoK8J+MkfCfjJLwn4yT8J+MlPCfjJXwn4yW8J+Ml/CfjJjwn4yZ8J+MmvCfjJvwn4yc8J+MnQplbW9qaeawtOaenCjpnZ7lm77niYflj6/lpI3liLYpCuKGkei/lOWbnumhtumDqAoK8J+Nh/CfjYjwn42J8J+NivCfjYvwn42M8J+NjfCfjY7wn42P8J+NkPCfjZHwn42S8J+NkwplbW9qaemSseW4gSjpnZ7lm77niYflj6/lpI3liLYpCuKGkei/lOWbnumhtumDqAoK8J+StPCfkrXwn5K28J+St/CfkrDwn5K48J+SswplbW9qaeS6pOmAmijpnZ7lm77niYflj6/lpI3liLYpCuKGkei/lOWbnumhtumDqAoK8J+agvCfmoPwn5qE8J+ahfCfmobwn5qH8J+aiPCfmonwn5qK8J+anfCfmp7wn5qL8J+ajPCfmo3wn5qO8J+aj/CfmpDwn5qR8J+akvCfmpPwn5qU8J+alfCfmpbwn5qX8J+amPCfmprwn5qb8J+anPCfmrLim73wn5qo8J+apfCfmqbwn5qn4pqT4pu18J+ao/CfmqTwn5qi4pyI8J+SuvCfmoHwn5qf8J+aoPCfmqHwn5qACmVtb2pp5bu6562RKOmdnuWbvueJh+WPr+WkjeWItikK4oaR6L+U5Zue6aG26YOoCgrwn4+g8J+PofCfj6Lwn4+j8J+PpPCfj6Xwn4+m8J+PqPCfj6nwn4+q8J+Pq/Cfj6zwn4+t8J+Pr/Cfj7Dwn5KS8J+XvPCfl73im6rwn4yG8J+Mh/CfjIkKZW1vamnlip7lhawo6Z2e5Zu+54mH5Y+v5aSN5Yi2KQrihpHov5Tlm57pobbpg6gKCvCfk7Hwn5Oy4piO8J+TnvCfk5/wn5Og8J+Ui/CflIzwn5K78J+SvfCfkr7wn5K/8J+TgPCfjqXwn5O68J+Tt/Cfk7nwn5O88J+UjfCflI7wn5Ss8J+UrfCfk6Hwn5OU8J+TlfCfk5bwn5OX8J+TmPCfk5nwn5Oa8J+Tk/Cfk4Pwn5Oc8J+ThPCfk7Dwn5OR8J+UlvCfkrPinInwn5On8J+TqPCfk6nwn5Ok8J+TpfCfk6bwn5Or8J+TqvCfk6zwn5Ot8J+TruKcj+KckvCfk53wn5OB8J+TgvCfk4Xwn5OG8J+Th/Cfk4jwn5OJ8J+TivCfk4vwn5OM8J+TjfCfk47wn5OP8J+TkOKcgvCflJLwn5ST8J+Uj/CflJDwn5SRCmVtb2pp566t5aS0KOmdnuWbvueJh+WPr+WkjeWItikK4oaR6L+U5Zue6aG26YOoCgrirIbihpfinqHihpjirIfihpnirIXihpbihpXihpTihqnihqripLTipLXwn5SD8J+UhPCflJnwn5Sa8J+Um/CflJzwn5Sd`
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
      /*box-shadow: 0 0 6px #888888;*/
      box-shadow: 4px 0 6px #888888;


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
          /*user-modify: read-write-plaintext-only;*/
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
