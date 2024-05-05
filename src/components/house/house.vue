<template>
    <div class="house">
        <floor v-for="n in floorCount" :number="n" 
        :currentFloor="currentFloor" 
        :floorNext="floorNext" 
        @addToQueue="addToQueue(n)" :key="n" />
    </div>
</template>

<script>
import Floor from "./floor.vue"

export default {
    name: "House",
    components: {
        Floor,
    },
    props: {
        floorCount: Number,
        floor: Number,
    },
    methods: {
        addToQueue(number) {
            this.$emit('addToQueue', number);
        }
    }
}
</script>


<style lang="scss" scoped>
.house {
    display: flex;
    flex-direction: column-reverse;
    width: 100%
}
</style>
