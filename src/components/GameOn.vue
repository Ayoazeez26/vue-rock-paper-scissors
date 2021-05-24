<template>
  <div class="flex justify-between items-center">
    <div class="player-hand relative mr-10 flex-flex-col">
      <p class="uppercase text-center text-white mb-5 text-xl">you picked</p>
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
    <div v-if="getResState" class="judge-set">
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
    <div class="house-hand relative ml-10 flex-flex-col">
      <p class="uppercase text-center text-white mb-5 text-xl">
        the house picked
      </p>
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
