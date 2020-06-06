<template>
  <v-list-item two-line>
    <v-list-item-content>
      <v-list-item-title>Weakness</v-list-item-title>
      <v-list-item-avatar v-for="(weakness, index) in weaknesses" :key="index">
        <Avatar :avatar="weakness.type" />
        {{weakness.value}}
      </v-list-item-avatar>
    </v-list-item-content>

    <v-list-item-content>
      <v-list-item-title>Resistance</v-list-item-title>
      <v-list-item-avatar v-for="(resistance, index) in resistances" :key="index">
        <Avatar :avatar="resistance.type" />
        {{resistance.value}}
      </v-list-item-avatar>
    </v-list-item-content>

    <v-list-item-content>
      <v-list-item-title>Retreat Cost</v-list-item-title>
      <v-list-item-avatar v-for="(rCost, index) in retreatCost" :key="index">
        <Avatar :avatar="rCost" />
      </v-list-item-avatar>
    </v-list-item-content>
  </v-list-item>
</template>

<script>
import Avatar from '../common/avatar.vue'
export default {
  name: 'PokemonDisabilities',
  props: ['weaknesses', 'resistances', 'retreatCost'],
  components: {
    Avatar
  }
}
</script>

<style>
</style>
