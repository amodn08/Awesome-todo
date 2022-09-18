<template>
  <q-layout view="hHh lpR fFf">
    <q-header elevated>
      <q-toolbar class="glossy">
        <q-toolbar-title class="absolute-center"> Awesome Todo</q-toolbar-title>

        <div></div>
      </q-toolbar>
    </q-header>

    <q-footer>
      <q-toolbar class="glossy">
        <q-tabs>
          <q-route-tab
            v-for="nav in navs"
            :key="nav.label"
            :to="nav.to"
            :icon="nav.icon"
            :label="nav.label"
          />
        </q-tabs>
      </q-toolbar>
    </q-footer>

    <q-drawer
      v-model="leftDrawerOpen"
      :breakpoint="767"
      show-if-above
      :width="250"
      bordered
      content-class="bg-primary"
    >
      <q-list dark>
        <q-item-label header class="text-grey-8"> Navigation </q-item-label>
        <q-item
          class="text-grey-4"
          v-for="nav in navs"
          :key="nav.label"
          exact
          :to="nav.to"
          clickable
        >
          <q-item-section avatar>
            <q-icon :name="nav.icon" />
          </q-item-section>
          <q-item-section>
            <q-item-label>{{ nav.label }}</q-item-label>
          </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
export default {
  name: "MainLayout",
  data() {
    return {
      leftDrawerOpen: false,
      navs: [
        {
          label: "Todo",
          icon: "list",
          to: "/",
        },
        {
          label: "Settings",
          icon: "settings",
          to: "/Settings",
        },
        {
          label: "About",
          icon: "info",
          to: "/about",
        },
      ],
    };
  },
};
</script>

<style lang="scss">
@media screen and (min-width: 767px) {
  .q-footer {
    display: none;
  }
}
.q-drawer {
  q-router-link--exact-active {
    color: white !important;
  }
}
</style>
