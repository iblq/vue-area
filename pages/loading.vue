<template>
  <div class="demo-loading">
    <divider>加载类型</divider>
    <fe-loading/>
    <fe-loading type="spinner"/>

    <divider>自定义颜色</divider>
    <fe-loading color="#1989fa"/>
    <fe-loading type="spinner" color="#1989fa"/>

    <divider>自定义大小</divider>
    <fe-loading color="#1989fa" size="50px"/>
    <fe-loading type="spinner" color="#1989fa" size="50px"/>

    <!-- <divider>文字</divider>
    <fe-loading>加载中...</fe-loading>-->
  </div>
</template>
<script>
import loading from "../src/Loading";
import divider from "../src/divider";
export default {
  name: "Loading",
  components: {
    "fe-loading": loading,
    divider: divider
  }
};
</script>
<style lang="less">
.demo-loading {
  .fe-loading {
    margin: 5px 0 5px 20px;
    display: inline-block;
  }
}
</style>

