<template>
  <button
    :style="buttonStyle"
    class="fe-button"
    :class="classList"
    :disabled="disabled"
    :type="actionType"
    @click="onClick"
  >
    <!-- <i class="fe-loading" /> -->
    <fe-loading size="20px" color="#fff" class="fe-button-loading" v-if="showLoading"/>
    <slot>{{ text }}</slot>
  </button>
</template>
<script>
import { go } from "../utils/router.js";
import loading from "../Loading";
export default {
  name: "FeButton",
  components: {
    "fe-loading": loading
  },
  props: {
    type: {
      type: String,
      default: "default"
    },
    disabled: {
      type: Boolean,
      default: false
    },
    mini: {
      type: Boolean,
      default: false
    },
    round: {
      type: Boolean,
      default: false
    },
    square: {
      type: Boolean,
      default: false
    },
    plain: {
      type: Boolean,
      default: false
    },
    text: {
      type: String,
      default: ""
    },
    actionType: {
      type: String,
      default: "submit"
    },
    showLoading: {
      type: Boolean,
      default: false
    },
    link: {
      type: [String, Object],
      default: ""
    },
    gradients: {
      type: Array,
      validator: function(val) {
        return val.length === 2;
      },
      default: function() {}
    }
  },
  computed: {
    noBorder() {
      return Array.isArray(this.gradients);
    },
    buttonStyle() {
      if (this.gradients && this.gradients.length) {
        return {
          background: `linear-gradient(90deg, ${this.gradients[0]}, ${
            this.gradients[1]
          })`,
          color: "#FFFFFF"
        };
      }
    },
    classList() {
      return [
        {
          "fe-button-disabled": !this.plain && this.disabled,
          "fe-button-plain-disabled": this.plain && this.disabled,
          "fe-button-mini": this.mini,
          "fe-button-round": this.round,
          "fe-button-square": this.square,
          "fe-button-noBorder": this.noBorder
        },
        !this.plain ? `fe-button-${this.type}` : "",
        this.plain ? `fe-button-plain-${this.type}` : "",
        this.showLoading ? `fe-button-loading` : ""
      ];
    }
  },
  methods: {
    onClick() {
      !this.disabled && go(this.link, this.$router);
    }
  }
};
</script>
<style lang="less">
@import "../style/var";

.fe-button {
  position: relative;
  padding: 0;
  display: inline-block;
  height: @button-default-height;
  line-height: @button-default-height;
  border-radius: @button-default-border-radius;
  box-sizing: border-box;
  font-size: 16px;
  width: 100%;
  text-align: center;
  -webkit-appearance: none;
  -webkit-text-size-adjust: 100%;
  outline: none;
  & + .fe-button {
    margin-top: 15px;
  }

  &::before {
    content: " ";
    position: absolute;
    top: 50%;
    left: 50%;
    opacity: 0;
    width: 100%;
    height: 100%;
    border: inherit;
    border-color: @black;
    background-color: @black;
    border-radius: inherit; /* inherit parent's border radius */
    transform: translate(-50%, -50%);
  }

  &:active::before {
    opacity: 0.15;
  }

  &-noBorder {
    border: 0 none;
  }

  &-loading,
  &-disabled {
    &::before {
      display: none;
    }
  }

  &-loading {
    display: inline-block;
    vertical-align: top;
  }

  &-default {
    color: @button-default-color;
    background-color: @button-default-background-color;
    border: 1px solid @button-default-border-color;
  }

  &-primary {
    color: @button-primary-color;
    background-color: @button-primary-background-color;
    border: 1px solid @button-primary-border-color;
  }

  &-danger {
    color: @button-danger-color;
    background-color: @button-danger-background-color;
    border: 1px solid @button-danger-border-color;
  }

  &-warn {
    color: @button-warning-color;
    background-color: @button-warning-background-color;
    border: 1px solid @button-warning-border-color;
  }

  &-plain {
    background-color: @white;

    &-default {
      background-color: @white;
      background-color: @button-default-background-color;
      border: 1px solid @button-default-border-color;
    }

    &-primary {
      background-color: @white;
      color: @button-primary-background-color;
      border: 1px solid @button-primary-border-color;
    }

    &.fe-button-danger {
      color: @button-danger-background-color;
    }

    &.fe-button-warning {
      color: @button-warning-background-color;
    }
  }

  &-mini {
    display: inline-block;
    width: 50px;
    height: 22px;
    line-height: 20px;
    font-size: 10px;

    & + .fe-button-mini {
      margin-left: 5px;
    }
  }

  &-bottom-action {
    width: 100%;
    height: 50px;
    line-height: 50px;
    border: 0;
    border-radius: 0;
    font-size: 16px;
    color: @button-bottom-action-default-color;
    background-color: @button-bottom-action-default-background-color;

    &.fe-button-primary {
      background-color: @button-bottom-action-primary-background-color;
    }
  }

  &-disabled {
    opacity: 0.5;
  }

  &-round {
    border-radius: 10em;
  }

  &-square {
    border-radius: 0;
  }
}
</style>
