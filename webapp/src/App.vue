<template>
  <div id="app">
    <div class="player-area">
      <player-area @card-hovered="highlightCard" :state="gameState.opponent" position="top"></player-area>
      <player-area @card-hovered="highlightCard" :state="gameState.player" position="bottom" draggable="true"></player-area>
    </div>
    <div class="info-area">
      <div class="card-highlight">
        <card :card="highlightedCard"></card>
      </div>
    </div>
  </div>
</template>

<script>
import PlayerArea from './components/PlayerArea'
import Card from './components/Card'

export default {
  name: 'App',
  components: {
    PlayerArea,
    Card
  },
  data: function () {
    return {
      gameState: {},
      highlightedCard: 'cardback'
    }
  },
  methods: {
    highlightCard: function (card) {
      this.highlightedCard = card
    }
  },
  created: function () {
    this.gameState = {
      player: {
        battle: ['Tropico', 'BoneSpider'],
        mana: ['BurningMane'],
        shield: ['KingCoral', 'DarkRavenShadowofGrief']
      },
      opponent: {
        battle: ['BloodySquito', 'BolshackDragon'],
        mana: ['BrawlerZyler'],
        shield: ['Meteosaur']
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
  width: calc(60% - 16px);
  height: calc(100% - 16px);
  position: absolute;
  left: 0;
  top: 0;
  padding: 8px;
  background: #666;
}

#app > .info-area {
  width: calc(40% - 16px);
  height: calc(100% - 16px);
  position: absolute;
  right: 0;
  top: 0;
  padding: 8px;
  background: #888;
  display: flex;
  justify-content: center;
}

#app .info-area .card-highlight > .card {
  width: 250px;
}

#app .info-area .card-highlight > img {
  width: 100%;
}

</style>
