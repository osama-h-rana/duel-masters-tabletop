<template>
  <div class="card-zone">
    <card
      v-for="(card, index) in cards"
      :key="index"
      :card="card"
      :flipped="flipped"
      :untappable="untappable"
      @mouseover.native="flipped ? null : $emit('card-hovered', card)"
      draggable
      @dragstart.native="$emit('drag-card', $event, card, index)"
    >
    </card>
    <card v-if="cards.length == 0" card="cardback" class="no-show"></card>
  </div>
</template>

<script>
import Card from './Card.vue'
export default {
  components: { Card },
  name: 'CardZone',
  props: ['cards', 'flipped', 'untappable'],
  data () {
    return {
    }
  }
}
</script>

<style scoped>
div.card-zone {
  display: flex;
  width: 100%;
  justify-content: center;
  min-height: 20px;
  background: #333;
  border: solid 1px black;
}

div.player-area.top .card-zone {
  transform: rotate(180deg);
}

div.player-area > .card-zone.mana {
  transform: rotate(180deg);
}

div.player-area.top > .card-zone.mana {
  transform: rotate(0deg);
}

</style>
