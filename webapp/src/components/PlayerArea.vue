<template>
  <div class="player-area" :class="position">
    <card-zone :cards="state.battle" class="battle"></card-zone>
    <card-zone :cards="state.shield" class="shield"></card-zone>
    <card-zone :cards="state.mana" class="mana"></card-zone>
  </div>
</template>

<script>
import CardZone from './CardZone.vue'
export default {
  components: { CardZone },
  name: 'PlayerArea',
  props: ['position', 'state'],
  data () {
    return {
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
