<script setup lang="ts">
import { computed } from 'vue'

// Props
export interface Props {
  drawer?: boolean
  rail?: boolean
}
const props = withDefaults(defineProps<Props>(), {
  drawer: true,
  rail: true
})

// Computed values
const propDrawer = computed(() => {
  return props.drawer
})
const propRail = computed(() => {
  return props.drawer
})
</script>

<template>
  <v-layout>
    <v-navigation-drawer v-model="propDrawer" :rail="rail" permanent @click="propRail = false">
      <v-list-item
        prepend-avatar="https://randomuser.me/api/portraits/men/85.jpg"
        title="John Leider"
        nav
      >
        <template v-slot:append>
          <v-btn variant="text" icon="mdi-chevron-left" @click.stop="propRail = !propRail"></v-btn>
        </template>
      </v-list-item>

      <v-divider></v-divider>

      <v-list density="compact" nav>
        <v-list-item prepend-icon="mdi-home-city" title="Home" value="home"></v-list-item>
        <v-list-item prepend-icon="mdi-account" title="My Account" value="account"></v-list-item>
        <v-list-item
          prepend-icon="mdi-account-group-outline"
          title="Users"
          value="users"
        ></v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-main style="height: 250px"></v-main>
  </v-layout>
</template>
