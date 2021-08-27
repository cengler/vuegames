<template>
  <div class="card shadow-5" :class="flippedStyles" @click="selectCard">
    <div class="card-face is-front">
      <img
        class="card-image"
        :srcset="`/images/${value}@2x.png 2x, /images/${value}.png 1x`"
        :src="`/images/${value}.png`"
        :alt="value"
      />
      <img v-if="matched" src="/images/checkmark.svg" class="icon-checkmark" />
    </div>
    <div class="card-face is-back"
         :style="{ backgroundImage: 'url(/images/' + deckFace + ')' }"></div>
  </div>
</template>

<script>
import { computed } from 'vue'

export default {
  props: {
    matched: {
      type: Boolean,
      default: false
    },
    position: {
      type: Number,
      required: true
    },
    value: {
      type: String,
      required: true
    },
    visible: {
      type: Boolean,
      default: false
    },
    deckFace: {
      type: String,
      required: true
    }
  },
  setup(props, context) {
    const flippedStyles = computed(() => {
      if (props.visible) {
        return 'is-flipped'
      }
      return ''
    })

    const selectCard = () => {
      context.emit('select-card', {
        position: props.position,
        faceValue: props.value
      })
    }

    return {
      flippedStyles,
      selectCard
    }
  }
}
</script>

<style>
.card {
  position: relative;
  transition: 0.5s transform ease-in;
  transform-style: preserve-3d;
  border-radius: 10px;
}

.card.is-flipped {
  transform: rotateY(180deg);
}

.card-face {
  width: 100%;
  height: 100%;
  position: absolute;
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  backface-visibility: hidden;
}

.card-face.is-front {
  background-color: white;
  color: white;
  transform: rotateY(180deg);
}

.card-face.is-back {
  background-size: 100%;
  color: white;
}

.card-image {
  max-width: 100%;
}

.icon-checkmark {
  position: absolute;
  right: 5px;
  bottom: 5px;
}
</style>
