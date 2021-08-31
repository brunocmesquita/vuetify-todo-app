<template>
  <v-app id="inspire">
    <v-navigation-drawer app v-model="drawer" :mobile-breakpoint="768">
      <v-img
        class="pa-4  pt-7"
        src="../public/montains.jpg"
        height="170"
        color="primary"
        gradient="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)"
      >
        <v-avatar size="70" class="mb-2">
          <img src="../public/profile.jpeg" alt="Bruno" />
        </v-avatar>
        <div class="white--text text-subtitle-1 font-weight-bold">
          Bruno Mesquita
        </div>
        <div class="white--text text-subtitle-2">brunocmesquita</div>
      </v-img>

      <v-list dense nav>
        <v-list-item v-for="item in items" :key="item.title" :to="item.to" link>
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar
      app
      prominent
      height="170"
      color="primary"
      shrink-on-scroll
      dark
      src="../public/montains.jpg"
    >
      <template v-slot:img="{ props }">
        <v-img
          v-bind="props"
          gradient="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)"
        ></v-img>
      </template>
      <v-container class="header-container pa-0">
        <v-row>
          <v-app-bar-nav-icon @click="toogleDrawer"></v-app-bar-nav-icon>
          <v-spacer></v-spacer>
          <search></search>
        </v-row>
        <v-row>
          <v-app-bar-title class="ml-4">Vuetify Todo</v-app-bar-title>
        </v-row>
        <v-row>
          <live-date-time></live-date-time>
        </v-row>
      </v-container>
    </v-app-bar>
    <v-main>
      <router-view></router-view>
      <snackbar></snackbar>
    </v-main>
  </v-app>
</template>

<script>
export default {
  data: () => ({
    drawer: null,
    items: [
      { title: 'To Do', icon: 'mdi-format-list-checks', to: '/' },
      { title: 'About', icon: 'mdi-help-box', to: '/about' },
    ],
    right: null,
  }),
  methods: {
    toogleDrawer() {
      this.drawer = !this.drawer;
    },
  },
  components: {
    snackbar: require('@/components/Shared/Snackbar.vue').default,
    search: require('@/components/Tools/Search.vue').default,
    'live-date-time': require('@/components/Tools/LiveDateTime.vue').default,
  },
};
</script>

<style lang="sass">
.header-container
  max-width: none !important
</style>
