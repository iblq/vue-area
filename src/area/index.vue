<template>
          <div class="fe-area">
    <div class="title">{{title}}</div>
    <div class="content">
      <div class="header">

      </div>
      <div class="col-wrap">
        <div>
          <ul id="example-1">
            <li v-for="item in list" :key="item">
              {{ item }}
            </li>
          </ul>
        </div>
      </div>
    </div>
</div>

</template>

<script>
// import { go } from "../utils/router.js";
import popup from './popup';
export default {
  name: "area",
//   components: {
//     "fe-popup": popup
//   },
data(){
    console.log(this);
    return {listsss: [1,3,4,5,6,2,4]}
},
  props: {
    title: {
      type: String,
      default: "title"
    },
    value: {
      type: Object,
      default: null
    },
    list: {
      type: Object,
      default: ()=>{}
    },
    "item-height": {
      type: [Number, String],
      default: 40
    },
    "columns-num": {
      type: [Number, String],
      default: 3
    },
    "on-change": {
      type: Function,
      default: ()=>{}
    },
    "on-cancel": {
      type: Function,
      default: ()=>{}
    },
    "on-confirm": {
      type: Function,
      default: ()=>{}
    },
    "on-show": {
      type: Function,
      default: ()=>{}
    },
  },
  computed: {
    noBorder() {
      return Array.isArray(this.gradients);
    },
  },
  methods: {
    onClick() {
      !this.disabled && go(this.link, this.$router);
    }
  }
}
</script>
<style lang="less">
@import "../style/var";
@import "./style";


</style>
