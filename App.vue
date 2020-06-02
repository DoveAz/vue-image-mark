<template>
  <div>
    <Draw :pointList="pointList" @pointClick="pointClick" @add="handleAdd"></Draw>
  </div>
</template>
<script>
import Draw from './Draw'

export default {
  components: {Draw},
  data() {
    return {
      pointList: []
    }
  },
  methods: {
    handleAdd(point){
      console.log(111)
      this.pointList.push(point)
    },
    pointClick(){
      console.log(222)
    }
  }
}
</script>
<style lang="less">

</style>
