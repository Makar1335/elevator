<template>
  <input type="number" v-model="floorCount">
  <div class="app">
    <elevatorfloor :currentFloor="currentFloor" :floorNext="floorNext" />
    <house :floorCount="floorCount" :currentFloor="currentFloor" :floorNext="floorNext" @addToQueue="addToQueue" />
  </div>
</template>

<script>
import elevatorfloor from "./components/elevator/elevatorfloor.vue";
import House from "./components/house/house.vue";
export default {
  name: "App",
  components: {
    House,
    elevatorfloor,
  },
  data() {
    return {
      floorCount: 5,
      currentFloor: 1,
      floorNext: 1,
      queue: [],
      isMoving: false,
    };
  },
  methods: {
    changeFloor(number) {
      this.currentFloor = number;
    },
    clearQueue() {
      this.queue = [];
      console.log("Очередь очищена.");
    },
    addToQueue(floorNext) {
      if (!this.queue.includes(floorNext) && floorNext !== this.currentFloor) {
        this.queue.push(floorNext);
        console.log(`Этаж ${floorNext} добавлен в очередь`);

        if (!this.isMoving) {
          this.processQueue();
        }
      } else {
        console.log(`Этаж ${floorNext} уже в очереди или является текущим этажом`);
      }
    },
    processQueue() {
      if (this.queue.length > 0) {
        if (!this.isMoving) {
          this.isMoving = true;

          const nextFloor = this.queue.shift();
          console.log(`Лифт движется на этаж ${nextFloor}`);
          this.currentFloor = nextFloor;

          setTimeout(() => {
            console.log(`Лифт прибыл на этаж ${nextFloor}`);
            this.floorNext = nextFloor;
            this.isMoving = false;
            this.processQueue(); // Рекурсивный вызов для обработки следующих этажей
          }, 5000); // Имитация времени движения лифта (5 секунды) 
        } else {
          console.log('Лифт уже находится в движении');
        }
      } else {
        console.log('Очередь пуста');
        if (this.currentFloor != 1) {
          setTimeout(() => {
          console.log(`Лифт спускается на первый этаж`)
          this.addToQueue(1);
        }, 10000);
        }
      }
    }

  },
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
}

.app {
  display: flex;
}
</style>
