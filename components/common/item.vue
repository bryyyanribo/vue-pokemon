<template>
  <v-list-item two-line>
    <v-list-item-avatar class v-for="(avatar, index) in cost" :key="index">
      <Avatar :avatar="avatar" />
    </v-list-item-avatar>

    <v-list-item-content>
      <v-list-item-title>{{name}}</v-list-item-title>
      <v-list-item-subtitle class="text-wrap">{{text}}</v-list-item-subtitle>
    </v-list-item-content>

    <v-list-item-action>
      <v-list-item-title>{{ damage }}</v-list-item-title>
    </v-list-item-action>
  </v-list-item>
</template>

<script>
import Avatar from './avatar.vue'
export default {
  name: 'Item',
  components: {
    Avatar
  },
  props: ['cost', 'name', 'text', 'damage']
}
</script>

