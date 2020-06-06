<template>
  <v-container v-if="Object.entries(pokemon).length">
    <v-row align="center" justify="center">
      <v-col cols="12" xs="4" sm="4" md="4" lg="4">
        <h3 class="d-inline">{{ pokemon.name }}</h3>
        <div class="d-inline">
          <span>{{ pokemon.hp || 0 }}HP</span>
          <div class="d-inline" v-for="(type, index) in pokemon.types" :key="index">
            <Avatar :avatar="type" />
          </div>
        </div>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12" offset-sm="4" offset-md="4" xs="4" sm="4" md="4" lg="4">
        <v-img :src="pokemon.imageUrl"></v-img>
      </v-col>
    </v-row>
    <v-row>
      <v-col
        v-for="(attack, index) in pokemon.attacks"
        :key="index"
        cols="12"
        xs="12"
        sm="12"
        md="12"
        lg="12"
      >
        <PokemonAbilities
          :cost="attack.cost"
          :name="attack.name"
          :text="attack.text"
          :damage="attack.damage"
        />
      </v-col>
    </v-row>

    <v-row>
      <v-col cols="12" xs="12" sm="12" md="12" lg="12">
        <PokemonDisabilities
          :weaknesses="pokemon.weaknesses"
          :resistances="pokemon.resistances"
          :retreatCost="pokemon.retreatCost"
        />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import axios from 'axios'
import PokemonAbilities from '../../components/pokemon/pokemon-abilities.vue'
import PokemonDisabilities from '../../components/pokemon/pokemon-disablities.vue'
import Avatar from '../../components/common/avatar.vue'
export default {
  name: 'PokeInfo',
  components: {
    PokemonAbilities,
    PokemonDisabilities,
    Avatar
  },
  data: () => ({
    pokemon: {}
  }),
  async created() {
    const pokeInfo = await axios.get(
      `https://api.pokemontcg.io/v1/cards/${this.$route.params.id}`
    )
    this.pokemon = pokeInfo.data.card
  }
}
</script>

<style></style>
