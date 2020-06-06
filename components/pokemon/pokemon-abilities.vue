<template>
  <v-container>
    <v-row>
      <v-col>
        <Item :cost="cost" :name="name" :text="text" :damage="damage" />
      </v-col>
    </v-row>
  </v-container>
</template>

<script lang="ts">
import Item from '../common/item.vue'

export default {
  name: 'PokemonAbilities',
  components: {
    Item
  },
  props: ['cost', 'name', 'text', 'damage']
}
</script>
