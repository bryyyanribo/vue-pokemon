<template>
  <v-hover v-slot:default="{ hover }" open-delay="200">
    <v-card :elevation="hover ? 16 : 2" class="mx-auto">
      <nuxt-link :to="`/${pokemon.id}`">
        <v-img :src="pokemon.imageUrl" height="300px"></v-img>
      </nuxt-link>

      <v-card-actions>
        <v-card-subtitle>{{pokemon.name}}</v-card-subtitle>

        <v-spacer></v-spacer>
        <div v-for="(type, index) of pokemon.types" :key="index">
          <Chip :data="type" />
        </div>
      </v-card-actions>
    </v-card>
  </v-hover>
</template>

<script>
import Chip from '../../components/common/chips.vue'

export default {
  name: 'PokeCard',
  components: {
    Chip
  },
  props: ['pokemon']
}
</script>

<style>
</style>
