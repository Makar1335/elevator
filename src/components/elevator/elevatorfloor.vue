<template>
    <div class="elevatorFloor">
        <cabin :currentFloor="currentFloor" :floorNext="floorNext"/>
    </div>
</template>

<script>
import cabin from './cabin.vue';
export default {
    name: "elevatorFloor",
    data() {

    },
    components: {
        cabin
    },
    props: {
        currentFloor:Number,
        floorNext:Number,
    },
}
</script>
<style lang="scss" scoped>
.elevatorFloor {
    width: 150px;
    background-color: rgba(43, 45, 148, 0.5);
    position: relative;
}
</style>