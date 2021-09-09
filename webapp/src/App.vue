<template>
  <div id="app">
    <div class="player-area">
      <player-area :state="gameState.opponent" position="top"></player-area>
      <player-area :state="gameState.player" position="bottom"></player-area>
    </div>
  </div>
</template>

<script>
import PlayerArea from './components/PlayerArea'

export default {
  name: 'App',
  components: {
    PlayerArea
  },
  data: function () {
    return {
      gameState: {}
    }
  },
  created: function () {
    this.gameState = {
      player: {
        battle: ['AuraBlast', 'BoneSpider'],
        mana: ['BurningMane'],
        shield: ['cardback', 'cardback']
      },
      opponent: {
        battle: ['BloodySquito', 'BolshackDragon'],
        mana: ['BrawlerZyler'],
        shield: ['cardback']
      }
    }
  }
}
</script>

<style>
body {
  height: 100%;
  width: 100%;
  margin: 0;
  background: #888;
}

#app > .player-area {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  width: calc(60% - 8px);
  height: calc(100% - 8px);
  position: absolute;
  left: 0;
  top: 0;
  margin: 4px;
  background: #666;
}

</style>
