<template>
  <div class="card-zone">
    <card v-for="card in cards" :key="card" :card="card"></card>
  </div>
</template>

<script>
import Card from './Card.vue'
export default {
  components: { Card },
  name: 'CardZone',
  props: ['cards'],
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
