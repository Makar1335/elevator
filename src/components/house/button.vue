<template>
    <button class="floorButton" 
    :class="{'floorButton-waiting' : isWaiting}"
    @click="addToQueue" 
    >
        {{ number }}
    </button>
</template>

<script>
export default {
    name: "FloorButton",
    data() {
        return {
            isWaiting: false
        }
    },
    props: {
        number: Number,
        currentFloor: Number,
        floorNext: Number,
    },
    methods:{
        addToQueue(){
            this.$emit('addToQueue', this.number);
        }
    }
};
</script>

<style lang="scss" scoped>
.floorButton{
    width: 30px;
    height: 30px;
    border-radius: 50%;
    background-color: white;
    border: 0;
    &:hover{
        color: white;
        background-color: black;
        transition: all 0.5s ;
    }
    &-waiting{
        background-color: rgba(0, 151, 167, 0.5);
        &:hover{
            background-color: rgba(0, 151, 167, 0.5);
        }
    }
}
</style>