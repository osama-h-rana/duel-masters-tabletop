<template>
  <div class="card" @click="untappable ? null : tap = !tap" :class="{ 'tapped': tap, 'tappable': !untappable }">
    <img v-if="!flipped" :src="'./static/cards/' + card + '.jpg'">
    <img v-if="flipped" :src="'./static/cards/cardback.jpg'">
  </div>
</template>

<script>
export default {
  name: 'Card',
  data () {
    return {
      tap: false
    }
  },
  props: ['card', 'flipped', 'untappable']
}
</script>

<style scoped>
div.card {
  margin: 0px 4px;
  width: 80px;
  transition: all linear 0.2s;
}

div.card.tappable {
  margin: 0px 16px;
}

div.card > img {
  width: 100%;
  border-radius: 5%;
  pointer-events: none;
}

div.card.tapped {
  transform: rotate(90deg);
}

div.card.no-show {
  border: dashed 1px #777;
  background: #333;
  pointer-events: none;
}

div.card.no-show > img {
  opacity: 0;
}

</style>
