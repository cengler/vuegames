<template>
  <button v-if="newPlayer" @click="startNewGame" :class="$style.button" :style="{backgroundColor: color }">
    <img class="icon-play" src="/images/play.svg" alt="Play Icon"/>
    Start Game
  </button>
  <button v-else @click="startNewGame" :class="$style.button" :style="{backgroundColor: color }">
    <img src="/images/restart.svg" alt="Restart Icon" />
    Restart Game
  </button>
</template>

<script>

export default {
  props: {
    newPlayer: {
      type: Boolean,
      default: true
    },
    color: {
      type: String,
      required: false
    }
  },
  setup(props, ctx) {
    const startNewGame = () => {
      ctx.emit('start-new-game')
    }
    return {
      startNewGame
    }
  }
}
</script>

<style module>
.button {
  color: white;
  padding: 8px 16px 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 30px;
  font-weight: bold;
  font-family: 'Titillium Web', sans-serif;
  font-size: 1rem;
  border: 0;
  border-radius: 10px;
}

.button img {
  padding-right: 12px;
  transition: 0.2s opacity ease-in;
}

.button .icon-play {
  position: absolute;
  left: -6px;
  opacity: 1;
}

.button-icon {
  position: relative;
  width: 24px;
  height: 24px;
}
</style>
