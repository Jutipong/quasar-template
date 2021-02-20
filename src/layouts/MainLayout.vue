<template>
  <q-layout view="hHh LpR fFf" class="bg-grey-1">
    <q-header elevated class="text-dark bg-blue-8">
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          @click="leftDrawerOpen = !leftDrawerOpen"
          aria-label="Menu"
          icon="menu"
        />

        <!-- <q-btn flat no-caps no-wrap class="q-ml-xs" v-if="$q.screen.gt.xs">
          <q-icon :name="fabYoutube" color="red" size="28px" />
          <q-toolbar-title shrink class="text-weight-bold">
            YouTube
          </q-toolbar-title>
        </q-btn>-->

        <q-space />
        <q-btn round flat>
          <q-avatar size="26px">
            <img src="https://cdn.quasar.dev/img/boy-avatar.png" />
          </q-avatar>
          <q-tooltip>Account</q-tooltip>
        </q-btn>
        <div class="q-gutter-sm row items-center no-wrap">
          <q-btn round dense flat color="text" icon="apps">
            <q-tooltip>Apps</q-tooltip>
          </q-btn>
        </div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      content-class="bg-grey-2"
      :width="240"
    >
      <q-scroll-area class="fit">
        <q-list padding>
          <div v-for="(group, index) in menus" :key="index">
            <q-item-label header class="text-weight-bold text-uppercase">
              <q-icon :name="group.icon" />
              {{ group.title }}
            </q-item-label>
            <q-item v-for="link in group.links" :key="link.route" v-ripple clickable>
              <q-item-section avatar>
                <q-icon color="grey" :name="link.icon" />
              </q-item-section>
              <q-item-section>
                <q-item-label>{{ link.text }}</q-item-label>
              </q-item-section>
            </q-item>
            <!-- <q-separator class="q-mt-md q-mb-xs" />  -->
            <q-separator inset class="q-my-sm" />
          </div>
        </q-list>
      </q-scroll-area>
    </q-drawer>
    <q-page-container>
      <!-- <div class="q-pa-md q-gutter-sm">
        <q-breadcrumbs class="text-orange" active-color="secondary">
          <template v-slot:separator>
            <q-icon size="1.0em" name="arrow_forward" color="orange" />
          </template>
          <q-breadcrumbs-el label="Home" icon="home" />
          <q-breadcrumbs-el label="Components" icon="widgets" />
        </q-breadcrumbs>
      </div>-->

      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { fabYoutube } from '@quasar/extras/fontawesome-v5'
export default {
  name: "MyLayout",
  data() {
    return {
      leftDrawerOpen: false,
      menus: [
        {
          title: "Home demo",
          icon: 'home',
          links: [
            { icon: "videogame_asset", text: "demo1", route: "demo1" },
          ],
          active: false
        },
        {
          title: "Home demo 2",
          icon: 'home',
          links: [
            { icon: "home", text: "demo2", route: "demo2" }
          ],
          active: false
        },
      ],
    };
  },
  created() {
    this.fabYoutube = fabYoutube;
  },
};
</script>
