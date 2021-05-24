<template>
  <div class="pt-5 flex flex-col items-center">
    <header
      class="
        px-6
        py-5
        border
        flex
        items-center
        justify-between
        rounded-2xl
        w-1/2
      "
    >
      <nav>
        <img src="../assets/img/logo.svg" alt="logo" />
      </nav>
      <div
        class="
          scoreboard
          flex flex-col
          items-center
          bg-white
          rounded-lg
          py-4
          h-full
          w-32
        "
      >
        <p class="uppercase text-sm">score</p>
        <p class="score text-5xl font-bold">
          {{ getScore ? getScore : 0 }}
        </p>
      </div>
    </header>
    <div class="gameplay mt-5">
      <pick-hand v-if="!getGameState" />
      <game-on v-if="getGameState" />
    </div>
    <button
      class="
        uppercase
        text-white text-lg
        border
        py-2
        px-10
        rounded-lg
        absolute
        bottom-10
        right-20
        tracking-wider
      "
      id="show-modal"
      @click="showModal = !showModal"
    >
      Rules
    </button>
    <modal v-if="showModal" @close="showModal = !showModal" />
  </div>
</template>

<script>
import GameOn from "./GameOn.vue";
import Modal from "./Modal.vue";
import PickHand from "./PickHand.vue";
import { mapGetters } from "vuex";

export default {
  components: { PickHand, Modal, GameOn },
  data() {
    return {
      showModal: false,
    };
  },
  computed: {
    ...mapGetters(["getGameState", "getScore"]),
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
header {
  border: 2px solid #606e85;
}
.scoreboard > p {
  color: #2a46c0;
}
p.score {
  color: #3b4363;
}
</style>
