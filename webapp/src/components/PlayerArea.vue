<template>
  <div class="player-area" :class="position">
    <card-zone
      :cards="state.battle"
      class="battle"
      @card-hovered="x => $emit('card-hovered', x)"
      @drag-card="(evt, card, index) => startDragCard('battle', evt, card, index)"
      @dragend.native="x => endDragCard('battle', x)"
      @drop.native="x => dropCard('battle', x)"
      @dragover.native.prevent
      @dragenter.native.prevent
    >
    </card-zone>
    <card-zone
      :cards="state.shield"
      flipped="true"
      untappable="true"
      class="shield"
      @card-hovered="x => $emit('card-hovered', x)"
      @drag-card="(evt, card, index) => startDragCard('shield', evt, card, index)"
      @dragend.native="x => endDragCard('shield', x)"
      @drop.native="x => dropCard('shield', x)"
      @dragover.native.prevent
      @dragenter.native.prevent
    >
    </card-zone>
    <card-zone
      :cards="state.mana"
      class="mana"
      @card-hovered="x => $emit('card-hovered', x)"
      @drag-card="(evt, card, index) => startDragCard('mana', evt, card, index)"
      @dragend.native="x => endDragCard('mana', x)"
      @drop.native="x => dropCard('mana', x)"
      @dragover.native.prevent
      @dragenter.native.prevent
    >
    </card-zone>
  </div>
</template>

<script>
import CardZone from './CardZone.vue'
export default {
  components: { CardZone },
  name: 'PlayerArea',
  props: ['position', 'state', 'draggable'],
  data () {
    return {
    }
  },
  methods: {
    startDragCard: function (zone, evt, card, index) {
      if (!this.draggable) return
      evt.dataTransfer.dropEffect = 'move'
      evt.dataTransfer.effectAllowed = 'move'
      evt.dataTransfer.setData('card', card)
      evt.dataTransfer.setData('index', index)
    },
    endDragCard: function (zone, evt) {
      if (!this.draggable) return
      if (evt.dataTransfer.dropEffect === 'move') {
        const index = parseInt(evt.dataTransfer.getData('index'))
        this.state[zone].splice(index, 1)
      }
    },
    dropCard: function (zone, evt) {
      if (!this.draggable) return
      const card = evt.dataTransfer.getData('card')
      this.state[zone].push(card)
      evt.stopPropagation()
    }
  }
}
</script>

<style scoped>
div.player-area {
  width: 100%;
  display: flex;
  flex-direction: column;
}

div.player-area.top {
  flex-direction: column-reverse;
}

</style>
