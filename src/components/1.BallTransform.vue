<!-- 小球移动的组件 -->
<template>
  <div class="containerApp">
    <span :style="positionSpan"></span>
  </div>
</template>

<script>
export default {
  name: "BallTransformVue",
  data() {
    return {
      leftNum: "",
      topNum: "",
      positionSpan: {
        position: "absolute",
        top: 0 + "px",
        left: 0 + "px",
      },
      timer: null,
    };
  },
  mounted() {
    this.timer = setInterval(() => {
      this.leftNum = this.positionSpan.left.slice(
        0,
        this.positionSpan.left.length - 2
      );
      this.topNum = this.positionSpan.top.slice(
        0,
        this.positionSpan.top.length - 2
      );
      this.positionSpan.left = Number(this.leftNum) + 0.4 + "px";
      this.positionSpan.top = Number(this.topNum) + 0.1 + "px";
      console.log(this.topNum);
      if (Number(this.topNum) > 600) {
        clearInterval(this.timer);
      }
    }, 2);
  },
};
</script>
<style scoped lang="less">
.containerApp {
  margin: 0;
  padding: 0;
  span {
    display: block;
    width: 20px;
    height: 20px;
    background-color: red;
    border-radius: 50%;
  }
}
</style>
