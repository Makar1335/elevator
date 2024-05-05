<template>
  <div class="floor">
    <floorButton :number="number" 
    :currentFloor="currentFloor" 
    :floorNext="floorNext" 
    @addToQueue="addToQueue" />
    <div class="floor__content">
      <!-- <img src="../pepega.png" alt=""> -->
    </div>
  </div>
</template>

<script>
import FloorButton from "./button.vue"

export default {
  name: "Floor",
  components: {
    FloorButton,
  },
  data() {
  },
  props: {
    number: Number,
    currentFloor: Number,
    floorNext: Number,
  },
  methods: {
    addToQueue() {
      this.$emit('addToQueue', this.number);
    }
  }
}
</script>

<style lang="scss" scoped>
.floor {
  display: flex;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  align-items: center;
  &__content{
    height: 150px;
    width: 100%;
    //background-color: antiquewhite;
    //border-bottom: 1px solid black;
    img{
      height: 150px;
    }
  }
  
}
</style>