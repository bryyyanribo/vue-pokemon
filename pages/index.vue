<template>
  <v-layout>
    <v-container>
      <v-row v-if="Object.entries(pokemons).length">
        <v-col v-for="pokemon in pokemons" :key="pokemon.id" cols="12" xs="12" sm="4" md="4" lg="3">
          <PokeCard :id="pokemon.id" :pokemon="pokemon" />
        </v-col>
        <v-pagination v-model="page" class="my-4" :length="15" :total-visible="7" @input="loadData"></v-pagination>
      </v-row>
    </v-container>
  </v-layout>
</template>

<script>
import axios from 'axios'
import PokeCard from '../components/pokemon/pokemon-card.vue'

export default {
  components: {
    PokeCard
  },
  data: () => ({
    pokemons: [],
    page: 1
  }),
  created() {
    this.loadData(this.page)
  },
  methods: {
    async loadData(page) {
      try {
        const pokeList = await axios.get(
          `https://api.pokemontcg.io/v1/cards?page=${page}`
        )
        this.pokemons = pokeList.data.cards
      } catch (e) {
        this.pokemons = []
        throw e
      }
    }
  }
}
</script>
