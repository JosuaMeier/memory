<template>
  <div class="card" v-bind:class="{ turnaround: showBack }">
    <v-card class="front">
      <v-container fill-height>
        <v-layout row wrap align-center>
          <v-flex class="text-xs-center">
            {{front}}
          </v-flex>
        </v-layout>
      </v-container>
    </v-card>
    <v-card class="back">
      <v-container fill-height>
        <v-layout row wrap align-center>
          <v-flex class="text-xs-center">
            {{back}}
          </v-flex>
        </v-layout>
      </v-container>
    </v-card>
  </div>
</template>

<script>
  export default {
    name: 'Memory',
    props: ['front', 'back', 'showBack'],
    methods: {
      clickCard(index) {
        this.cards[index].visible = !this.cards[index].visible;
      }
    }
  }
</script>

<style scoped>
  @font-face { font-family: 'Black';
    src: url('../assets/black.ttf') format('truetype'); }

  .card {
    display: block;
    transition: transform .8s;
    transform-style: preserve-3d;
    position: relative;
    height: 100%;
    perspective: 1500px;
    -moz-backface-visibility: hidden;
    font-size: 80px;
  }

  .application .theme--light.v-card, .theme--light .v-card {
    color: #777 !important;
    font-family: Black, Times, serif;
  }

  .application .theme--light.v-card, .theme--light .v-card.back {
    font-family: "Arial Black", Times, serif !important;
    color: #eee !important;
    background: darkcyan;
  }

  .card.turnaround {
    transform: rotateY(180deg);
  }

  .front,
  .back {
    backface-visibility: hidden;
    position: absolute;
    width: 100%;
    height: 100%;
    box-sizing: border-box;
    background: white;
  }

  .front {
    z-index: 2;
  }

  .back {
    transform: rotateY(180deg);
    z-index: 1;
  }
</style>
