<template>
  <v-avatar>
    <v-img :src="`pokemon-icon/${imageUrl}.png`" :alt="imageUrl"></v-img>
  </v-avatar>
</template>

<script>
export default {
  name: 'Avatar',
  props: ['avatar'],
  data: () => ({
    imageUrl: ''
  }),
  created() {
    console.log(this.avatar)
    this.imageUrl = this.avatar != undefined ? this.avatar.toLowerCase() : ''
  }
}
</script>
