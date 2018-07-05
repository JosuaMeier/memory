<template>
  <div @keyup.67="clear()">
    <v-layout row wrap>
      <v-flex v-for="(card, index) in cards" :key="index" xs3 @click="clickCard(index)">
        <FlipCard
                class="flip-card"
                v-bind:class="{ 'invisible': card.finished }"
                :front="index + 1"
                :back="card.value"
                :showBack="card.visible"></FlipCard>
      </v-flex>
    </v-layout>
  </div>
</template>

<script>
  import FlipCard from './FlipCard'

  export default {
    name: 'Memory',
    components: {
      FlipCard
    },
    data() {
      return {
        cards: [
          {visible: false, finished: false, value: 'B'}, {visible: false, finished: false, value: 'X'},
          {visible: false, finished: false, value: 'M'}, {visible: false, finished: false, value: 'S'},
          {visible: false, finished: false, value: 'D'}, {visible: false, finished: false, value: 'Y'},
          {visible: false, finished: false, value: 'W'}, {visible: false, finished: false, value: 'Z'},
          {visible: false, finished: false, value: 'T'}, {visible: false, finished: false, value: 'E'},
          {visible: false, finished: false, value: 'A'}, {visible: false, finished: false, value: 'H'},
          {visible: false, finished: false, value: 'I'}, {visible: false, finished: false, value: 'V'},
          {visible: false, finished: false, value: 'O'}, {visible: false, finished: false, value: 'Q'},
          {visible: false, finished: false, value: 'N'}, {visible: false, finished: false, value: 'U'},
          {visible: false, finished: false, value: 'C'}, {visible: false, finished: false, value: 'F'},
        ]
      }
    },
    methods: {
      clickCard(index) {
        this.cards[index].visible = !this.cards[index].visible;
      }
    },
    mounted: function() {
      window.addEventListener('keydown', (event) => {
        // If down arrow was pressed...
        if (event.keyCode == 67) {
          this.cards = this.cards.map((card) => card.visible ? {...card, finished: true} : card);
        }
      });
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .flip-card {
    height: calc(20vh - 60px);
    margin: 30px;
    cursor: pointer;
  }
  .invisible {
    visibility: hidden;
  }
</style>
