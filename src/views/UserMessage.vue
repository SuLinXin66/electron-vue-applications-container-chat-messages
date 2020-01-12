<template>
  <div class="user-messages">

  </div>
</template>

<script lang="ts">
  import {Component, Prop, Vue} from "vue-property-decorator";
  import {UserInfo} from "@/types/user";

  @Component({})
  export default class UserMessage extends Vue {

    @Prop({type: Object, required: true})
    private nowUser!: UserInfo;

    @Prop({type: Object, required: true})
    private toUser!: UserInfo;



  }
</script>

<style scoped>

</style>
