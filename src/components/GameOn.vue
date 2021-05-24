<template>
  <div class="flex flex-wrap justify-between items-center">
    <div class="player-hand relative mr-5 md:mr-10 flex-flex-col">
      <p class="hidden md:block uppercase text-center text-white mb-5 text-xl">
        you picked
      </p>
      <div class="relative h-40 w-36">
        <div class="absolute">
          <hand :class="getPlayerHand">
            <img
              slot="handImage"
              :src="playerImg(getPlayerHand)"
              :alt="getPlayerHand"
            />
            <div
              slot="handAfter"
              :class="getPlayerHand + '-semi'"
              class="semi"
            ></div>
          </hand>
        </div>
      </div>
      <p class="block md:hidden uppercase text-center text-white mt-5 text-xl">
        you picked
      </p>
    </div>
    <div
      v-if="getResState"
      class="
        judge-set
        flex flex-col
        items-center
        order-last
        md:order-none
        w-full
        mt-20
        md:mt-0
        md:w-auto
      "
    >
      <h1 class="text-4xl text-white text-center font-bold mb-5 uppercase">
        {{ getResult }}
      </h1>
      <button
        @click="replaySet"
        class="bg-white text-lg score uppercase hover:text-red-400 px-10 py-2"
      >
        play again
      </button>
    </div>
    <div class="house-hand relative ml-5 md:ml-10 flex-flex-col">
      <p class="hidden md:block uppercase text-center text-white mb-5 text-xl">
        the house picked
      </p>
      <div class="relative h-40 w-36">
        <div class="absolute">
          <div
            v-if="!getHouseState"
            class="houseTemp h-40 w-40 rounded-full bg-black opacity-40"
          ></div>
          <hand v-if="getHouseState" :class="getHouseHand">
            <img
              slot="handImage"
              :src="houseImg(getHouseHand)"
              :alt="getHouseHand"
            />
            <div
              slot="handAfter"
              :class="getHouseHand + '-semi'"
              class="semi"
            ></div>
          </hand>
        </div>
      </div>
      <p class="md:hidden uppercase text-center text-white mt-5 text-xl">
        the house picked
      </p>
    </div>
  </div>
</template>

<script>
import Hand from "./Hand.vue";
import { mapGetters, mapActions } from "vuex";

export default {
  components: { Hand },
  data() {
    return {
      handType: "rock",
    };
  },
  computed: {
    ...mapGetters([
      "getPlayerHand",
      "getHouseHand",
      "getHouseState",
      "getResult",
      "getResState",
    ]),
  },
  methods: {
    playerImg(hand) {
      return require("../assets/img/icon-" + hand + ".svg");
    },
    houseImg(hand) {
      return require("../assets/img/icon-" + hand + ".svg");
    },
    ...mapActions(["replaySet"]),
  },
};
</script>

<style lang="scss" scoped></style>
