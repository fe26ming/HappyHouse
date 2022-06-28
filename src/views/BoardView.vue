<template>
  <b-container class="bv-example-row mt-3 text-center">
    <br /><br />
    <h3 class="underline-hotpink">
      <b-icon icon="journals" class="board-icon"></b-icon> 게시판
    </h3>
    <router-view></router-view>
  </b-container>
</template>
<script>
export default {
  name: "BoardView",
};
</script>
<style scoped>
.underline-hotpink {
  font-weight: bold;
  color: cornflowerblue;
}
.board-icon {
  color: black;
}
</style>
