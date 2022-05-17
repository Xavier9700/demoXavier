<!--Menu latéral-->
<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title>
          Quasar Application
        </q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
    >
      <q-list>
        <q-item-label
          header
        >
          Mes exercices
        </q-item-label>
        <q-item
          v-for="lienPage of liens"
          :key="lienPage.url"
          :to="lienPage.url"
          clickable
          v-ripple
          active
        >
          <q-item-section avatar>
            <q-icon :name="lienPage.icon" />
          </q-item-section>
          <q-item-section>{{ lienPage.nom }}</q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from 'vue'

export default defineComponent({
  name: 'MainLayout',
  // Emplacement du tableau de données
  data () {
    return {
      liens: [{
        nom: 'Exercice 1',
        url: '/ex1',
        icon: 'face'
      },
      {
        nom: 'Exercice 2',
        url: '/ex2',
        icon: 'fastfood'
      }
      ]
    }
  },
  components: {

  },

  setup () {
    const leftDrawerOpen = ref(false)

    return {
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  }
})
</script>
