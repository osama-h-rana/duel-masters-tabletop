<template>
  <div class="card">
    <img :src="image_url">
  </div>
</template>

<script>
export default {
  name: 'Card',
  data () {
    return {
      image_url: null
    }
  },
  props: ['card'],
  created: function () {
    this.image_url = './static/cards/' + this.card + '.jpg'
  }
}
</script>

<style scoped>
div.card {
  margin: 0px 4px;
  width: 80px;
}

div.card > img {
  width: 100%;
}

</style>
