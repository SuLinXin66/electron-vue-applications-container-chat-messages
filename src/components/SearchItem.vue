<template>
  <div class="search-item">
    <Input search placeholder="Enter something..." />
  </div>
</template>

<script lang="ts">
  import {Component, Vue} from "vue-property-decorator";
  import {Input} from "view-design";

  @Component({components:{Input}})
  export default class SearchItem extends Vue{

  }
</script>

<style scoped>

</style>
