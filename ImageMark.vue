<template>
  <div class="image-mark">
    <img :src="imageSrc" alt="" @click="handleBoardClick" />
    <ul class="point-list">
      <li
        v-for="point in pointList"
        :key="point.id"
        :class="point.class"
        :style="{ top: point.y + '%', left: point.x + '%', ...pointStyle, backgroundColor: point.color }"
        @click="handlePointClick(point)"
      >
        {{ point.id }}
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  name: 'ImageMark',
  props: {
    pointList: {
      type: Array,
      required: true
    },
    pointStyle: {
      type: Object,
      default() {
        return {}
      }
    },
    imageSrc:{
      type:String,
      required:true
    }
  },
  data() {
    return {}
  },
  methods: {
    handleBoardClick(e) {
      let point = {}
      if (uni) {
        const query = uni.createSelectorQuery().in(this)
        query
          .select('.image-mark')
          .boundingClientRect(el => {
            point = {
              x: ((e.detail.x - el.left) / el.width) * 100,
              y: ((e.detail.y - el.top) / el.height) * 100,
              id: this.pointList.length + 1
            }
            this.$emit('add', point)
          })
          .exec()
      } else {
        point = {
          x: (e.layerX / e.target.width) * 100,
          y: (e.layerY / e.target.height) * 100,
          id: this.pointList.length + 1
        }
        this.$emit('add', point)
      }
    },
    handlePointClick(point) {
      this.$emit('pointClick', point)
    }
  }
}
</script>
<style lang="less">
.image-mark {
  position: relative;
  border: 1px solid #f006;
  width: 100%;

  img {
    width: 100%;
  }

  .point-list {
    list-style: none;
    margin: 0;

    li {
      z-index: 100;
      user-select: NONE;
      position: absolute;
      /* prettier-ignore */
      width: 26PX;
      /* prettier-ignore */
      height: 26PX;
      /* prettier-ignore */
      line-height: 26PX;
      background-color: #d7d7d7;
      border-radius: 50%;
      color: #fff;
      text-align: center;
      transform: translate(-50%, -50%);
    }
  }
}
</style>
