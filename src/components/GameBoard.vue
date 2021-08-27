<template>
  <transition-group tag="section" class="game-board" name="shuffle-card">
    <Card
      v-for="card in cardList"
      :key="`${card.value}-${card.variant}`"
      :matched="card.matched"
      :value="card.value"
      :visible="card.visible"
      :position="card.position"
      :deckFace="deckFace"
      @select-card="selectCard"
    />
  </transition-group>
  <h2 class="status">{{ status }}</h2>
</template>

<script>
import Card from './Card'

export default {
  components: {
    Card
  },
  props: {
    cardList: {
      type: Array,
      required: true
    },
    deckFace: {
      type: String,
      required: true
    },
    status: {
      type: String,
      required: true
    }
  },
  setup(props, ctx) {
    const selectCard = payload => {
      ctx.emit('flip-card', payload)
    }

    return {
      selectCard
    }
  }
}
</script>

<style>
.game-board {
  display: grid;
  grid-template-columns: repeat(4, 60px);
  grid-template-rows: repeat(4, 60px);
  grid-column-gap: 12px;
  grid-row-gap: 12px;
  justify-content: center;
}

@media screen and (min-width: 300px) {
  .game-board {
    grid-template-columns: repeat(4, 80px);
    grid-template-rows: repeat(4, 80px);
  }
}

@media screen and (min-width: 500px) {
  .game-board {
    grid-template-columns: repeat(4, 90px);
    grid-template-rows: repeat(4, 90px);
  }
}

@media screen and (min-width: 600px) {
  .game-board {
    grid-template-columns: repeat(4, 120px);
    grid-template-rows: repeat(4, 120px);
  }
}

.shuffle-card-move {
  transition: transform 0.8s ease-in;
}

</style>
