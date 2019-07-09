<template>
<fe-area />
</template>


<script>

import area from "../src/area";

export default {
  name: "Button",
  components: {
    "fe-area": area,
  },
  data() {
    return {
      list: [1,2,233,54,223,23,42,34,234,234,4,5,6,67,7,8,98]
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
