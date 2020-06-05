<template>
  <div class="mega-land-dealer">
    <transition name="component-fade" mode="out-in">
      <TheCard
        v-if="currentCard !== null"
        v-bind:card-url="currentCard"
        v-on:clicked="draw()"
      />
    </transition>
    <button v-on:click="draw()">Draw</button>
    <button v-on:click="shuffle()">Shuffle</button>
  </div>
</template>

<script>
import TheCard from "./TheCard";
const cards = [
  require("@/assets/images/card01.jpg"),
  require("@/assets/images/card02.jpg"),
  require("@/assets/images/card03.jpg"),
  require("@/assets/images/card04.jpg"),
  require("@/assets/images/card05.jpg"),
  require("@/assets/images/card06.jpg"),
  require("@/assets/images/card07.jpg"),
  require("@/assets/images/card08.jpg"),
  require("@/assets/images/card09.jpg"),
  require("@/assets/images/card10.jpg")
];

export default {
  components: {
    TheCard
  },
  name: "TheMegaLandDealer",
  data() {
    return {
      shownCards: [],
      currentCard: null
    };
  },
  props: {},
  methods: {
    isCardPresent() {
      return this.shownCards.lenth !== 0;
    },
    draw() {
      if (cards.length <= this.shownCards.length) {
        return;
      }
      let cardNumber = -1;
      while (this.shownCards.includes(cardNumber) || cardNumber === -1) {
        cardNumber = Math.floor(Math.random() * cards.length);
      }
      console.info("New Card = " + cardNumber);
      this.shownCards.push(cardNumber);
      this.currentCard = cards[cardNumber];
    },
    shuffle() {
      this.currentCard = null;
      this.shownCards = [];
    }
  },
  computed: {}
};
</script>

<style scoped>
div.mega-land-dealer {
  width: 50px;
  height: 50px;
}
</style>
