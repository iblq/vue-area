<template>
  <div :class="`fe-loading fe-loading-${type}`">
    <span :class="`fe-loading-inner--${type} fe-loading-inner`" :style="style">
      <i v-for="(item, index) in (type === 'spinner' ? 12 : 0)" :key="index"/>
      <svg v-if="type === 'circular'" class="fe-loading-icon-circular" viewBox="25 25 50 50">
        <circle cx="50" cy="50" r="20" fill="none"></circle>
      </svg>
    </span>
    <!-- <span class="fe-loading-text" v-if="$slots.default">
      <slot/>
    </span>-->
  </div>
</template>

<script>
const DEFAULT_COLOR = "#c9c9c9";
export default {
  name: "FeLoading",
  props: {
    size: String,
    type: {
      type: String,
      default: "circular"
    },
    // textSize: {
    //   type: [String, Number]
    // },
    color: {
      type: String,
      default: DEFAULT_COLOR
    }
  },
  computed: {
    colorType() {
      const { color } = this;
      return color === "white" || color === "black" ? color : "";
    },
    style() {
      return {
        color: this.color === "black" ? DEFAULT_COLOR : this.color,
        width: this.size,
        height: this.size
      };
    }
  }
};
</script>
<style lang="less">
@import "../style/var";
.fe-loading {
  position: relative;
  font-size: 0;
  vertical-align: middle;
  &-inner {
    position: relative;
    display: inline-block;
    width: 30px;
    max-width: 100%;
    height: 30px;
    max-height: 100%;
    vertical-align: middle;
    animation: fe-rotate 0.8s linear infinite;

    &--spinner {
      animation-timing-function: steps(12);

      i {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;

        &::before {
          display: block;
          width: 2px;
          height: 25%;
          margin: 0 auto;
          background-color: currentColor;
          border-radius: 40%;
          content: " ";
        }
      }
    }

    &--circular {
      animation-duration: 2s;
    }
  }
  &-icon-circular {
    display: block;
    width: 100%;
    height: 100%;

    circle {
      stroke: currentColor;
      stroke-width: 3;
      stroke-linecap: round;
      animation: fe-circular 1.5s ease-in-out infinite;
    }
  }
  &-text {
    display: inline-block;
    margin-left: 10px;
    color: #969799;
    font-size: 14px;
    vertical-align: middle;
  }

  &-circle {
    width: 16px;
    height: 16px;
  }

  &--white {
    .fe-loading-spinner--circle {
      border-color: rgba(0, 0, 0, 0.1);
      border-top-color: rgba(255, 255, 255, 0.7);
    }

    .fe-loading-spinner--gradient-circle {
      background-image: url("https://img.yzcdn.cn/fet/gradient-circle-white.png");
    }
  }
}

@keyframes fe-rotate {
  from {
    transform: rotate(0deg);
  }

  to {
    transform: rotate(360deg);
  }
}

@keyframes fe-circular {
  0% {
    stroke-dasharray: 1, 200;
    stroke-dashoffset: 0;
  }

  50% {
    stroke-dasharray: 90, 150;
    stroke-dashoffset: -40;
  }

  100% {
    stroke-dasharray: 90, 150;
    stroke-dashoffset: -120;
  }
}

.generate-spinner(@n, @i: 1) when (@i =< @n) {
  .fe-loading-inner--spinner i:nth-of-type(@{i}) {
    opacity: 1 - (0.75 / 12) * (@i - 1);
    transform: rotate(@i * 30deg);
  }
  .generate-spinner(@n, (@i + 1));
}
.generate-spinner(12);
</style>
