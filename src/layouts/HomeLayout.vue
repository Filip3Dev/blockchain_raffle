<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated class="bg-black">
      <q-toolbar>
        <q-btn flat @click="drawer = !drawer" round dense icon="menu" />
        <q-toolbar-title>
          Oxigen Lottery
        </q-toolbar-title>
      </q-toolbar>
    </q-header>
    <q-page-container>
      <router-view />
    </q-page-container>
    <q-drawer
      v-model="drawer"
      show-if-above
      :mini="!drawer || miniState"
      :width="250"
      :breakpoint="700"
      elevated
      content-class="bg-primary text-white"
    >
      <q-scroll-area class="fit">
        <div class="q-pa-sm">
          <div v-for="n in 50" :key="n">Drawer {{ n }} / 50</div>
        </div>
      </q-scroll-area>
    </q-drawer>
  </q-layout>
</template>

<script>
export default {
  name: 'HomeLayout',

  data () {
    return {
      drawerLeft: false,
      drawer: true,
      miniState: true
    }
  },
  methods: {

  }
}
</script>
