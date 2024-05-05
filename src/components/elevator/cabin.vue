<template>
    <div class="cabin"
        :style="'bottom:' + (currentFloor - 1) * 150 + 'px; transition-duration: ' + Math.abs(currentFloor - floorNext) + 's'">
    </div>
</template>

<script>
export default {
    name: "Cabin",
    date() {
    },
    props: {
        currentFloor: Number,
        floorNext: Number,
    },
    watch: {
        currentFloor(newVal, oldVal) {
            console.log("Изменение currentFloor:", newVal, oldVal);
        },
        floorNext(newVal, oldVal) {
            console.log("Изменение floorNext:", newVal, oldVal);
        },
    },
}
</script>

<style lang="scss" scoped>
.cabin {
    width: 100%;
    height: 150px;
    background-color: aqua;
    position: absolute;
    bottom: 0;
}
</style>