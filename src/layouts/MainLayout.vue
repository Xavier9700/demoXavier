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
          to="/ex1"
          clickable
          v-ripple
          active-class="my-menu-link"
        >
          <q-item-section avatar>
            <q-icon name="face" />
          </q-item-section>
          <q-item-section>Exercice 1</q-item-section>
        </q-item>
      </q-list>
      <router-link :to="{ path: 'ex1' }">Exercice1</router-link>
      <br>
      <router-link :to="{ path: 'ex2' }">Exercice2</router-link>
<!--      <router-link :to="{ path: '/' }">Home page</router-link>-->
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
        lien: '/ex1',
        icon: 'Face'
      },
      {
        nom: 'Exercice 2',
        lien: '/ex2',
        icon: 'euro_symbol'
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
