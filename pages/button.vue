<template>
  <div>
    <h1>{{msg}}</h1>
    <div style="margin:10px;">
      <divider>渐变</divider>
      <div class="buttons-big">
        <fe-button :gradients="['#1D62F0', '#19D5FD']">多彩渐变</fe-button>
      </div>
      <divider>默认</divider>
      <fe-button>submit</fe-button>
      <fe-button type="primary">primary</fe-button>
      <fe-button type="warn">Delete</fe-button>
      <fe-button type="danger">危险按钮</fe-button>

      <divider>link</divider>
      <fe-button type="primary" link="/">去主页</fe-button>
      <fe-button type="default" link="BACK">返回</fe-button>

      <divider>action type</divider>
      <fe-button type="primary" action-type="button">提交</fe-button>
      <fe-button type="warn" action-type="reset">重置</fe-button>
      <fe-button type="danger" action-type="reset">危险重置</fe-button>

      <divider>loading</divider>
      <fe-button type="default" show-loading>submit</fe-button>
      <fe-button type="primary" show-loading>submit</fe-button>
      <fe-button type="danger" show-loading>submit</fe-button>
      <fe-button type="warn" show-loading>submit</fe-button>

      <divider>小按钮</divider>
      <fe-button mini>submit</fe-button>
      <fe-button mini type="primary">primary</fe-button>
      <fe-button mini type="warn">删除</fe-button>
      <fe-button mini type="danger">删除</fe-button>
      
      <br>
      <fe-button mini plain>submit</fe-button>
      <fe-button mini plain type="primary">primary</fe-button>

      <divider>plain</divider>
      <fe-button plain>submit</fe-button>
      <fe-button plain type="primary">primary</fe-button>

      <divider>自定义样式</divider>
      <fe-button plain type="primary" square>方角 primary</fe-button>
      <fe-button plain type="primary" round >圆角 primary</fe-button>

      <divider>不可用状态</divider>
      <fe-button disabled>不可用的</fe-button>
      <fe-button type="primary" disabled>不可用的 primary</fe-button>
      <fe-button type="warn" disabled>不可用的删除</fe-button>
      <fe-button type="danger" disabled>不可用的删除</fe-button>

      <fe-button mini disabled>不可用</fe-button>
      <fe-button mini type="primary" disabled>不可用</fe-button>
      <fe-button mini type="warn" disabled>不可用</fe-button>
      <fe-button mini type="danger" disabled>不可用</fe-button>

      <fe-button plain disabled>不可用无背景</fe-button>
      <fe-button plain type="primary" disabled>disable plain primary</fe-button>

      <divider>点击不可用状态</divider>
      <fe-button
        :text="submit001"
        :disabled="disable001"
        @click.native="processButton001"
        type="primary"
      ></fe-button>
      <!-- <divider>和flexbox一起使用1</divider>
          <flexbox :gutter="0"> 
            <flexbox-item :span="2" style='text-align: center;'>
              <img src="https://m.axnsc.com/Contents/images/Shopping-2.png" alt="" style='width:20px'>
              <p style='font-size: 10px;margin-top: -5px;color: #808185;'>购物车</p>
            </flexbox-item>
            <flexbox-item>
              <fe-button type="primary" style="border-radius:0;background:#FE8604;">加入购物车</fe-button>
            </flexbox-item>
            <flexbox-item>
              <fe-button type="warn" style="border-radius:0;background:#FF3C25;">立即购买</fe-button>
            </flexbox-item>
          </flexbox>
          <divider>和flexbox一起使用2</divider>
          <flexbox>
            <flexbox-item>
              <fe-button type="primary">primary</fe-button>
            </flexbox-item>
            <flexbox-item>
              <fe-button type="warn">Delete</fe-button>
            </flexbox-item>
          </flexbox>
          <divider>和flexbox一起使用3</divider>
          <flexbox>
            <flexbox-item>
              <fe-button type="default">default</fe-button>
            </flexbox-item>
            <flexbox-item>
              <fe-button type="primary">primary</fe-button>
            </flexbox-item>
            <flexbox-item>
              <fe-button type="warn">Delete</fe-button>
            </flexbox-item>
      </flexbox>-->
    </div>
  </div>
</template>

<script>
import button from "../src/button";
import divider from "../src/divider";

export default {
  name: "Button",
  components: {
    "fe-button": button,
    divider: divider
  },
  data() {
    return {
      submit001: "点我呀",
      disable001: false,
      msg: "button"
    };
  },
  methods: {
    processButton001() {
      this.submit001 = "处理中...";
      this.disable001 = true;
    }
  }
};
</script>
