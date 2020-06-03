<template>
  <div>
    <ImageMark
      imageSrc="http://static.doveaz.xyz/img/2d.jpg"
      :pointList="pointList"
      @pointClick="pointClick"
      @add="handleAdd"
    ></ImageMark>
  </div>
</template>
<script>
import ImageMark from "./ImageMark";

export default {
  components: { ImageMark },
  data() {
    return {
      pointList: [],
    };
  },
  methods: {
    handleAdd(point) {
      console.log(111);
      this.pointList.push(point);
    },
    pointClick() {
      console.log(222);
    },
  },
};
</script>
<style lang="less"></style>
